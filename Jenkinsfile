pipeline {
   agent any
    stages {
       stage('git checkout'){
         steps {
             git 'https://github.com/prashanth19975/sample-web-nov.git'
           }
           }
       stage('mvn version') {
           steps {
               sh "mvn --version"
           }
           }
        stage('clean compile test package'){
           steps {
               sh "mvn clean compile test package"
           }
           }
         stage('mvn deploy') {
            steps {
                sh "mvn deploy"
          }
       }
         sshagent(['deploy-tomcat']) {
              sh "scp -o StrictHostkeyChecking=no webapp/target/sample-web.war ec2-user@13.234.66.30:/root/tomcat/webapps"

      
}
   
   }
}
