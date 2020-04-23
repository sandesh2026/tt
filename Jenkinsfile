#!/usr/bin/env groovy
import java.net.URL

node{
    stage('Git Checkout'){
        git 'https://github.com/sandesh2026/DevOpsClassCodes.git'
    }
    stage('AB compile'){
        withMaven(maven:'mymaven')
        {
        sh 'mvn compile'
        }
    }
    stage('Code review'){
        try {
        withMaven(maven:'mymaven')
        {
            sh 'mvn pmd:pmd'
        }
        }
        finally {
            pmd canComputeNew: false, defaultEncoding: '', healthy: '', pattern: 'target/pmd.xml', unHealthy: ''
        }
    }
    stage('AB Package'){
        withMaven(maven:'mymaven')
        {
        sh 'mvn package'
        }
    }
}
