pipeline {
    agent any
    tools {
        maven 'MAVEN3'
    }
    stages {
        stage("Build"){
            steps {
                    sh script :'mvn clean pacage'
                 }
            }   
        stage("upload nexus to war"){
            steps {
              nexusArtifactUploader artifacts: [
                  [
                      artifactId: 'simple-app',
                      classifier: '', 
                      file: 'targets/simple-app-3.0.0.war', 
                      type: 'war'
                      ]
                    ], 
                    credentialsId: 'nexusCredentials', 
                    groupId: 'in.javahome',
                    nexusUrl: '34.122.102.201:8081', 
                    nexusVersion: 'nexus3',
                    protocol: 'http', 
                    repository: 'verifierUIapp-release', 
                    version: '3.0.0'
            }
        }
    }   
}
