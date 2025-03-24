pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/stbestichhh/it-management-lab2.git', credentialsId: 'github'
            }
        }
        
        stage('Build') {
            steps {
                // Крок для збірки проекту з Visual Studio
                // Встановіть правильні шляхи до рішення/проекту та параметри MSBuild
                bat "\"C:\\Program Files\\Microsoft Visual Studio\\2022\\Community\\MSBuild\\Current\\Bin\\MSBuild.exe\" test_repos.sln /t:Build /p:Configuration=Debug"

            }

        }

        stage('Test') {
            steps {
                // Команди для запуску тестів
                bat "x64\\Debug\\test_repos.exe --gtest_output=xml:test_report.xml"
            }
        }
    }

    post {
      always {
        // Publish test results using the junit step
         // Specify the path to the XML test result Files\Microsoft
        junit '**/test_report.xml'
      }
    }
  }

