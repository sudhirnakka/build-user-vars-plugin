pipeline {
  stages {
    stage('compile') {
      steps {
        sh 'mvn clean install'
      }
    }
    stage('archive') {
      steps {
        parallel(
          "Junit": {
            junit 'target/surefire-reports/*.xml'
          },
          "Archive": {
            archiveArtifacts(artifacts: 'target/build-user-vars-plugin.jar', onlyIfSuccessful: true, fingerprint: true)
            archiveArtifacts(artifacts: 'target/build-user-vars-plugin.hpi', fingerprint: true)
          }
        )
      }
    }
  }
}
