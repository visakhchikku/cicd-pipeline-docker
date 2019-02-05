pipeline {
    agent any 
    stages {
  stage('Build') {
steps {
   echo 'Running build automation'
   sh ',/gradlew build --no-deamon'
   archiveArtifacts artifacts: 'dist/trainSchedule.zip'
  }
}
 stage('Build Docker Image') {
    when {
          branch 'master'
      }
     steps {
         script {
           app = docker.build("docker_password/node-app")
           app.inside {
                sh 'echo $(curl localhost:8080)'
}
}
}
}
  stage('Push Docker Image') {
      when {
            branch 'master'
        }
 steps {
    script {
        docker.withRegistry('https://registry.hub.docker.com','docker_password') {
        app.push("${env.BUILD_NUMBER}")
        app.push("latest")
       }
}
}
}
                            }
                            }
