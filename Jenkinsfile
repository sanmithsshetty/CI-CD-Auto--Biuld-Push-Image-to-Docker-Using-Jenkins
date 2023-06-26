pipeline {
    agent any 
    environment {
    DOCKERHUB_CREDENTIALS = credentials('sanmithsshetty-dockerhub')
    }
    stages { 

        stage('Build docker image') {
            steps {  
                sh 'docker build -t amc/flaskapp:$BUILD_NUMBER .'
            }
        }
        stage('login to dockerhub') {
            steps{
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-dckr_pat_ju2xfmG9NZ1Oe3B9OGEEzExAvBQ'
            }
        }
        stage('push image') {
            steps{
                sh 'docker push ylmt/flaskapp:$BUILD_NUMBER'
            }
        }
}
post {
        always {
            sh 'docker logout'
        }
    }
}
