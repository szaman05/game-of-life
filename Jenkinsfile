pipeline{
    agent any
    tools{
        jdk 'jdk-8'
    }
    stages{
        stage('Fetch'){
            steps{
                git branch:'master', url: 'https://github.com/wakaleo/game-of-life.git'
            }
         }
         stage('Build'){
            steps{
                sh 'mvn clean package'
            }
         }
         stage('Test'){
            junit '**/target/surefire-reports/*.xml'
         }
    }
    post{
         success{
            echo 'Archiving Artifacts now...'
            archiveArtifacts artifacts: '**/target/*.war'
        }
    }
}
