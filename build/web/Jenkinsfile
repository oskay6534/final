pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                checkout scmGit(
                    branches: [[name: '*/master']],
                    userRemoteConfigs: [[url: 'https://github.com/oskay6534/final.git']]
                )
            }
        }
        stage('Build docker image'){
            steps{
                script{
                    docker.build("final1:${env.BUILD_NUMBER}")
                }
            }
        }
        stage('Push image to Hub'){
            steps{
                script{
                    docker.image("ysmfinal:${env.BUILD_NUMBER}").run("-d -p 8090:8080 --name final-container")
                }
            }
  }
}

}