pipeline{
  agent any

stages{
  stage("Build"){
    steps{
      sh "run python3 app.py"
    }
  }

  stage("Test"){
    steps{
      echo "Running Tests..."
    }
  }

  stage("Build Docker"){
    steps{
      sh "docker build -t myapp ."
    }
  }

  stage("Deploy"){
    steps{
      sh '''
      docker stop myapp-container || true
      docker rm myapp-container || true
      docker run -d --name myapp-container -p 5000:5000 myapp
      '''
    }
  }

}
}
