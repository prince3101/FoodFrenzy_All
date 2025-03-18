pipeline{
    agent any

    tools{
        nodejs 'NodeJS'
    }

    environment{
        REPO_URL = "https://github.com/prince3101/Food_Frenzy_Dockerize.git"
    }

    stages{
        stage("clone"){
            steps{
                git url: "${REPO_URL}", branch: "main"
            }
        }
        stage("install"){
            steps{
                script{
                    dir('frontend'){
                        sh 'npm install'
                    }
                }

            }
        }
        stage('Test'){
            steps{
                script{
                    dir('frontend'){
                        sh 'npm test'
                    }
                    dir('backend'){
                        sh 'npm test'
                    }
                }
            }
        }
        stage('build'){
            steps{
                script{
                    dir('frontend'){
                        sh 'npm start'
                    }
                    dir('backend'){
                        sh 'npm start'
                    }
                }
            }
        }
    }
    post{
        always{
            echo "========always========"
        }
        success{
            echo "========pipeline executed successfully ========"
        }
        failure{
            echo "========pipeline execution failed========"
        }
    }
}