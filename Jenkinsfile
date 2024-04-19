pipeline {
  agent any

  stages {
    
    
    stage('Build Artifact') {
            steps {
              sh "mvn clean package -DskipTests=true"
              archive 'target/*.jar' //so that they can be downloaded later test aa
            }
        }   



//--------------------------
    stage('Docker Build and Push') {
      steps {
        withCredentials([string(credentialsId: 'password-dockerhub-nicolas', variable: 'DOCKER_HUB_PASSWORD')]) {
          sh 'sudo docker login -u pirox999056 -p $DOCKER_HUB_PASSWORD'
          sh 'printenv'
          sh 'sudo docker build -t pirox999056/devops-app:""$GIT_COMMIT"" .'
          sh 'sudo docker push pirox999056/devops-app:""$GIT_COMMIT""'
        }
 
      }
    }

    
    
    }
}
