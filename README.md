# Microservice with Kubernetes
Dockerize applications and deploy them by Kubernetes

## Prerequisites

Make sure you have installed all of the following prerequisites on your development machine:

- Minikube v1.14.1  | [minikube](https://minikube.sigs.k8s.io/docs/start/)
- Docker v19.03.12  | [docker](https://docs.docker.com/engine/install/)
- Kubernetes        | [kubernetes](https://kubernetes.io/vi/docs/tasks/tools/install-kubectl/) 

## Usage

##### Start minikube
```
username@computer:~$ minikube start --vm-driver virtualbox && minikube addons enable ingress
😄  minikube v1.14.1 on Darwin 10.15.5
✨  Using the virtualbox driver based on existing profile
👍  Starting control plane node minikube in cluster minikube
🔄  Restarting existing virtualbox VM for "minikube" ...
🐳  Preparing Kubernetes v1.19.2 on Docker 19.03.12 ...
🔎  Verifying Kubernetes components...
🔎  Verifying ingress addon...
🌟  Enabled addons: storage-provisioner, default-storageclass, ingress

❗  /usr/local/bin/kubectl is version 1.16.6-beta.0, which may have incompatibilites with Kubernetes 1.19.2.
💡  Want kubectl v1.19.2? Try 'minikube kubectl -- get pods -A'
🏄  Done! kubectl is now configured to use "minikube" by default
🔎  Verifying ingress addon...
🌟  The 'ingress' addon is enabled
```

##### Create deployment and services (it may take time)
```
username@computer:~/microservice-with-kubernetes$ kubectl apply -f database_mongo
username@computer:~/microservice-with-kubernetes$ kubectl apply -f database_sql_server
username@computer:~/microservice-with-kubernetes$ kubectl apply -f ncovidbackend
username@computer:~/microservice-with-kubernetes$ kubectl apply -f ncovidfrontend
username@computer:~/microservice-with-kubernetes$ kubectl apply -f phonebox
username@computer:~/microservice-with-kubernetes$ kubectl apply -f portfolio
username@computer:~/microservice-with-kubernetes$ kubectl apply -f store
username@computer:~/microservice-with-kubernetes$ kubectl apply -f ingress.yaml
```

##### Edit file hosts

Map minikube ip with domain in ingress

Check minikube ip
```
username@computer:~$ minikube ip
192.168.99.110
```

Append ip address to last file host
```
192.168.99.110   phonebox.kubernetes.thuanhong.io
192.168.99.110   store.kubernetes.thuanhong.io
192.168.99.110   portfolio.kubernetes.thuanhong.io
192.168.99.110   ncovid.kubernetes.thuanhong.io
```

Testing domain above on browser
