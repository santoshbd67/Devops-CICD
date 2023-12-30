pipeline {
    agent any
    tools{
        jdk 'jdk11'
        maven 'maven3'
    }
    environment{
	    SCANNER_HOME= tool "sonar-scanner"
    }
   

    stages {
        stage('git-checkout') {
            steps {
                git branch: 'main', changelog: false, poll: false, url: 'https://github.com/santoshbd67/Devops-CICD.git'
            }
        }
        
        stage('Code-Compile') {
            steps {
               sh "mvn clean compile"
            }
        }
        
       	stage('sonarqube analysis') {
	   steps {
		withSonarQubeEnv('sonar-scanner') {
			sh 'mvn sonar:sonar'
    		    
		}
	   }
	}
	
        stage('Code-Build') {
            steps {
               sh "mvn clean install"
            }
        }
       
        
    }
}
