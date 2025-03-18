pipeline {
    agent any

    stages {
	
        stage('clone GIT repo') {
            steps {
                echo 'cloning code from github repo'
				git branch: 'main', url: 'https://github.com/pranuthiruvva/mindcircuit15d.git'
            }
        }
		
		
		
		 stage('Build artifact') {
            steps {
                echo 'building artifact using maven build tool'
				sh 'mvn clean install'
            }
        }
		
		
		 stage('deploy to tomcat') {
            steps {
                echo 'deploying artifact on to tomcat'
				deploy adapters: [tomcat9(credentialsId: 'tomcat', path: '', url: 'http://ec2-3-80-106-98.compute-1.amazonaws.com:8081/')], contextPath: 'devops-app', war: '**/*.war'
            }
        }
    }
}
