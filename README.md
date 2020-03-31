# OKD/OCP Jenkins Pipeline Examples

## Prerequesites 

- a working OKD/OCP (see minishift or crc for test environment)
- a project namespace
- a jenkins instance deployed within the project namespace (not for Basic NGINX build)

## Basic NGINX build 

This example shows a basic external webhook from github after building a NGINX instance with the
"basic-html-page" directory. 

![preview](https://raw.githubusercontent.com/rovandep/ocp-nodejs-pipeline/master/images/basic-html-page-01.gif)
![preview](https://raw.githubusercontent.com/rovandep/ocp-nodejs-pipeline/master/images/basic-html-page-02.gif)

Repeat for a second 


== Simple nodejs example

This example is a quick and dirty way to show the usage of a buildconfig YAML file to create a 
Build Config within OKD/OCP that will use a Jenkins instance within the namespace to build
a simple ephemeral nodejs & mongodb instances with a working external route. 

To use it, it can be done through CLI: 
``` 
# oc create -f https://raw.githubusercontent.com/rovandep/ocp-nodejs-pipeline/master/nodejs-pipeline.yaml
# oc get buildconfig
NAME                     TYPE              FROM   LATEST
nodejs-pipeline          JenkinsPipeline          6

# oc start-build nodejs-pipeline
# oc get build
NAME                       TYPE              FROM          STATUS     STARTED          DURATION
nodejs-pipeline-1          JenkinsPipeline                 Complete   13 minutes ago   
``` 

It can be done through GUI too:
or from the project namespace Status or in Build Configs, click "Add, Import YAML" and copy/paste 
the contain of "nodejs-pipeline.yaml"

Once added, you can click the "Start Build" which will redirect you to the Build details. From that page,
the Jenkins pipeline job overview can be observed or click on "View Logs" to open Jenkins. 