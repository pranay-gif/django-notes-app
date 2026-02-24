@Library("Shared") _
pipeline{
    agent{
        label "vinod"
    }
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
                    clone("https://github.com/pranay-gif/django-notes-app.git","dev1")
                }
            }
        }
        stage("Build"){
            steps{
                script{
                    docker_build("notes-app","latest","pranaygarai")
                }
                 
            }
        }
         stage("Push to DockerHub"){
            steps{
                echo "This is Pushing image to Docker Hub"
                script{
                    docker_push("notes-app","latest","pranaygarai")
                }
                
            }
        }
        stage("Test"){
            steps{
                 echo "This is Testing the code"
            }
        }
        stage("Deploy"){
            steps{
                 echo "This is Deploying the code"
                 sh "docker compose up -d"
            }
        }
    }
}
