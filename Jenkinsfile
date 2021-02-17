pipeline{
    agent any

    tools{
        maven 'Maven'
        jdk 'jdk'
    }

    stages{
        stage('maven clean'){
            steps{
                bat 'mvn clean'
            }
        }

        stage('maven compile'){
            steps{
                bat 'mvn compile'
            }
        }

        stage('sonar analysis'){
            steps{
                withSonarQubeEnv('sonar-server'){
                    withMaven(maven:'Maven'){
                        bat 'mvn sonar:sonar'
                    }
                }
            }

        }

        stage('maven test'){
            steps{
                bat 'mvn test'
            }
        }

        stage('maven package'){
            steps{
                bat 'mvn package'
            }
        }
    }
}