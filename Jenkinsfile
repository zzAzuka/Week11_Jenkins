pipeline {
  agent any
  stages {
    stage('Clone') {
      steps {
        git branch: 'main', url: 'https://github.com/<your-username>/status-api.git'
      }
    }
    stage('Build Docker Image') {
      steps {
        script {
          bat 'docker build -t status-api .'
        }
      }
    }
    stage('Run Container') {
      steps {
        script {
          bat 'docker stop status-api || exit 0'
          bat 'docker rm status-api || exit 0'
          bat 'docker run -d -p 3000:3000 --name status-api status-api'
        }
      }
    }
  }
}
