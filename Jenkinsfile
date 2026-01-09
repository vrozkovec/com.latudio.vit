def targetServer = 'latudio-web'
def targetServerDirectory = '/data/webapps/www/com.latudio.vit/'
def repoName = 'com.latudio.vit'
def repoUrl = 'git@github.com:vrozkovec/com.latudio.vit.git'

pipeline {
	agent any
	options {
		disableConcurrentBuilds()
	}
	stages {
		stage('Pull repos') {
			parallel {
				stage('Production') {
					steps {
						ansiColor('xterm') {
							ansiblePullRemoteRepo (
								targetServer: targetServer,
								targetServerDirectory: targetServerDirectory,
								repoName: repoName,
								repoUrl: repoUrl,
								webserverWritableDirectoriesSemicolonSeparated: "cache;logs"
							)
						}
					}
				}
			}
		}
	}
}
