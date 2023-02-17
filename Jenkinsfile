pipeline {
  agent any
  stages {
    stage('clone repository') {
      steps {
        sh '''java -version
mvn --version
git --version'''
      }
    }
    stage('clean images') {
      steps {
        withCredentials(bindings: [
                      string(credentialsId: 'token-k8s-do', variable: 'api_token')
                      ]) {
            sh 'docker system prune --all --force'
          }
        }
      }
    }
  }
