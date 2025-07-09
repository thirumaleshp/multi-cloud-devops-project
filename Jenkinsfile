pipeline {
    agent any

    stages {
        stage('Clone Repo') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/thirumaleshp/multi-cloud-devops-project.git'
            }
        }

        stage('Deploy to Flask VM') {
            steps {
                sshagent(credentials: ['flask-ssh-credentials-id']) {
                    sh """
                        ssh -o StrictHostKeyChecking=no thirumaleshx@35.200.159.125  '
                            cd /home/thirumaleshx/multi-cloud-devops-project &&
                            git pull origin main &&
                            nohup python3 flask_app.py &
                        '
                    """
                }
            }
        }
    }
}
