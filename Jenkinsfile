 pipeline {
     agent any 
 tools {
 maven 'MAVEN_HOME' 
 }
 stages {
   stage('Build App') {
     steps {
       git branch: 'eap-7', url: 'https://github.com/sinanakyilmaz/openshift-tasks.git'
       sh "mvn clean package"
       }
	  }
	 }
	 post {
	     success {
	         echo 'Now Archiving...'
	         archiveArtifacts artifacts: '**/target/*.war'
	     }
	  }
   stage('Build Image') {
                steps {
                  sh "oc start-build  optask --from-file=target/ROOT.war --follow"
                }
              }  	  
            }
        
