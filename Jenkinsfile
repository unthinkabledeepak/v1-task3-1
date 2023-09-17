node {
    def app

    stage('Clone repository') {
      

        checkout scm
    }

    stage('Update GIT') {
            script {
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                    withCredentials([usernamePassword(credentialsId: 'github', passwordVariable: 'GIT_PASSWORD', usernameVariable: 'GIT_USERNAME')]) {
                    // withCredentials([string(credentialsId: 'github', variable: 'GITHUB_TOKEN')]) { 
                        
                        //def encodedPassword = URLEncoder.encode("$GIT_PASSWORD",'UTF-8')
                        sh "git config user.email deepak@unthinkable.co"
                        sh "git config user.name unthinkabledeepak"
                        //sh "git switch master"
                        sh "echo ${APPIMAGE}"
                        sh "cat values.yaml"
                        sh "sed -i 's+deepakc826/v1-task3:${APPIMAGE}.*+deepakc826/v1-task3:${APPIMAGE}-${DOCKERTAG}+g' values.yaml"
                        sh "cat values.yaml"
                        sh "git add ."
                        sh "git commit -m 'Done by Jenkins Job changemanifest: ${env.BUILD_NUMBER}'"
                        sh "git push https://${GIT_USERNAME}:${GIT_PASSWORD}@github.com/${GIT_USERNAME}/v1-task3.git HEAD:main"
                        // sh "git push https://${GITHUB_TOKEN}@github.com/${GIT_USER_NAME}/${GIT_REPO_NAME} HEAD:main"
                        // sh "git push https://${GITHUB_TOKEN}@github.com/${GIT_USERNAME}/${GIT_REPO_NAME} HEAD:main"
                        
      }
    }
  }
}
}
