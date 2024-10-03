@Library("Shared") _
pipeline{
    agent { label "vinod" }
    
    stages{
        
        stage("Hello"){
            steps{
                script{
                    hello()
                }
            }
        }
        stage("Code"){
            steps{
                script{
                    clone("https://github.com/priyankasaini69/notes-App-Django.git","main")
                }
            }
        }
        stage("Build"){
            steps{
                script{
                    docker_build("notes-app","latest","prisaini23")
                }
            }
        }
        stage("Push to DockerHub"){
            steps{
                script{
                    docker_push("notes-app","latest","prisaini23")
                }
            }
        }
        stage("Deploy"){
            steps{
                echo "This is Deploying the code"
                sh "docker compose down && docker compose up -d"
                echo "image run in a container successfully"
            }
        }
    }
}
