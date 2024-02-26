# githubactions-qckstrt
Quickstart for GitHub Actions
Variables
Variables provides a way to store and reuse non-sensitive configuration information.
you can store any configuration data such as compiler flags, usernames, or server names as variables.
Variables are interpolated on the runner machine that runs your workflow. 
There are two types of variables.
    1. default environment variables - refer this link >> https://docs.github.com/en/actions/learn-github-actions/variables#default-environment-variables
    2. custom environment variables 
        Custom veriables can be set in two ways.
        * you can define environemnt variables for single workflow.
        * you can define environment variables for multiple workflows

###############Example##########################

name: GitHub_Actions_Variable_Demo
run-name: ${{ github.actor }} is testing GitHub Action features
on: [push]
jobs:
    docker:
        runs-on: ubuntu-latest
        steps:
        - name: Docker Build
          run: docker build -t docker.io/dockerUsername/imageName:latest
        - name: Docker Login
          run: docker login --username=dockerUsername --password=010388
        - name: Docker Publish
          run: docker psuh docker.io/dockerUsername/imageName:latest
    
    deploy:
        runs-on: ubuntu-latest
        steps:
        - name: Creating a container
          run: docker run -d -p 8080:80 docker.io/dockerUsername/imageName:latest

#In above example we can see few information are being repeatative. In softrware development, we generally follow DRY(Don't Repeat Yourself) principle.          