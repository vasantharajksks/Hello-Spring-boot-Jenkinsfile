#!/usr/bin/env groovy

@Library('Shared-Library@master') _ //master or whatever branch

node{
   stage('SCM Checkout'){
       git branch: 'main', credentialsId: 'git-cred', url: 'https://github.com/vasantharajksks/Hello-Sprint-boot'
   }
   stage('Mvn Package'){
     def mvnHome = tool name: 'maven-3', type: 'maven'
     def mvnCMD = "${mvnHome}/bin/mvn"
     sh "${mvnCMD} clean package"
   }
   stage('Build Docker Image'){
     sh 'docker build -t my-app .'
   }
   
   stage ('Check logs') {
    steps {
       filterLogs ('WARNING', 5)
     }
   }
       
}
