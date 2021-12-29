pipeline {
  agent {
    kubernetes {
      label 'promo-app'  // all your pods will be named with this prefix, followed by a unique id
      idleMinutes 5  // how long the pod will live after no jobs have run on it
      yamlFile 'build.yaml'  // path to the pod definition relative to the root of our project 
      defaultContainer 'maven'  // define a default container if more than a few stages use it, will default to jnlp container
    }
  }
  stages {
 
    stage('Build Docker Image') {
      steps {
        container('terraform') {  
          sh "terraform init" // when we run docker in this step, we're running it via a shell on the docker build-pod container, 
          sh "terraform plan"

        }
      }
    }
  }
