pipeline {
  agent any

  parameters {
    choice(
      name: 'TARGET_ENV',
      choices: ['dev', 'test', 'prod'],
      description: 'Select target environment for backend deployment'
    )
  }

  environment {
    APP_NAME = 'backend-demo'
  }

  stages {

    stage('Validate Kubernetes Cluster') {
      steps {
        sh 'kubectl get nodes'
      }
    }

    stage('Backend Build (Placeholder)') {
      steps {
        echo 'Building backend application...'
        echo 'This stage will later compile Java / Python backend'
      }
    }

    stage('Unit Test (Placeholder)') {
      steps {
        echo 'Running backend unit tests...'
        echo 'This stage will later run JUnit / PyTest'
      }
    }

    stage('Deploy Backend') {
      steps {
        sh """
          echo "Deploying ${APP_NAME} to ${params.TARGET_ENV}"
          kubectl get namespace ${params.TARGET_ENV}
          echo "kubectl apply -n ${params.TARGET_ENV} -f k8s/backend/"
        """
      }
    }
  }

  post {
    success {
      echo "Backend deployment successful in ${params.TARGET_ENV}"
    }
    failure {
      echo "Backend deployment failed"
    }
  }
}
