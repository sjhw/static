pipeline {
  agent any
  stages {
    stage('Lint HTML') {
      steps {
        sh '''
          /usr/bin/tidy -q -e *.html
        '''
      }
    }
    stage('Upload to AWS') {
      steps {
        withAWS(region:'us-west-2',credentials:'aws-static') { 
          s3Upload(pathStyleAccessEnabled: true, payloadSigningEnabled: true, file:'index.html', bucket:'udacitydevops3.thruniverse.com', path:'index.html')
        }
      }
    }
  }
}
