pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'dotnet test tests/unitTestes'
      }
    }

    stage('Tests') {
      parallel {
        stage('Unit') {
          steps {
            sh 'dotnet test tests/unitTestes'
          }
        }

        stage('Integration') {
          steps {
            sh 'dotnet test tests/IntegrationTestes'
          }
        }

        stage('Functional') {
          steps {
            sh 'dotnet test tests/FunctionalTestes'
          }
        }

      }
    }

    stage('Deployment') {
      steps {
        sh 'dotnet publish eShopOnWeb -o /var/aspnet'
      }
    }

  }
}