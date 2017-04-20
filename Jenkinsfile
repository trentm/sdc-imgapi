pipeline {
    agent { label 'master:true' }

    environment {
        FOO = 'bar'
    }

    options {
        timeout(time: 1, unit: 'HOURS')
        timestamps()
    }

    parameters {
        string(name: 'BRANCH', defaultValue: 'master')
        string(name: 'TRY_BRANCH')
    }

    stages {
        stage('Preamble') {
            steps {
                echo 'Building...'
                echo "FOO envvar is '$FOO'"
                echo "BRANCH param is '${params.BRANCH}'"
                echo "TRY_BRANCH param is '${params.TRY_BRANCH}'"
                sh 'env'
            }
        }
        stage('Build') {
            steps {
                sh 'make release'
            }
        }
    }
}
