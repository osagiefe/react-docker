pipeline {
  agent any
  
   tools {nodejs "node"}
    
  stages {
    stage("Clone code from GitHub") {
            steps {
                script {
                    git branch: 'main', url: 'https://github.com/osagiefe/react-docker.git'
                }
            }
        }
     
    stage('Node JS Build') {
      steps {
        sh 'npm install'
      }
    }
  
     stage('Build Node JS Docker Image') {
            steps {
                script {
                  sh 'docker build -t osagiefe/node-app-1.0 .'
                }
            }
        }


        stage('Push Docker Image to DockerHub') {
            steps {
                script {
                 withCredentials([string(credentialsId: 'FelixID', variable: 'osagiefe')]) {
                    sh 'docker login -u osagiefe -p ${FelixID}'
            }
            sh 'docker push osagiefe/node-app-1.0'
        }
            }   
        }
         


  }
}