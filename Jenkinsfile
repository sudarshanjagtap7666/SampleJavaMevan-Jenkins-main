pipeline {
    agent any
    tools {
        maven 'MyMaven'
    }
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build') {
            steps {
                sh 'mvn clean install'
                stash name: 'jar-artifacts', includes: 'target/*.jar'
            }
        }
        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }
        stage('Archive'){
            steps {
                unstash 'jar-artifacts'
                archiveArtifacts artifacts: 'target/*.jar'
            }
        }
    }
}