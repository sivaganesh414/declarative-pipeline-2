pipeline {
   agent any

   tools {
      maven "maven3"
   }

   stages {
      stage('getscm') {
         steps {
		 
                git credentialsId: 'git_credentials', url: 'https://github.com/sivaganesh414/MavenBuild-1.git'
          
         }
      }
         
         stage('build'){
             
             steps{
                  
                 sh 'mvn package'
             }
         }
         
         stage('deploy') {
             steps{
                 sh "curl -v -u admin:admin -T /var/lib/jenkins/workspace/tomcat_deploy_pipeline/target/java-example.war 'http://ec2-18-220-8-150.us-east-2.compute.amazonaws.com:9090/manager/text/deploy?path=/pipeline_spring_curl'"
               
             }
             }
         }
   }
