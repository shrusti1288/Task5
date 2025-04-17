# Task5
Build a Kubernetes Cluster Locally with Minikube

Step 1: Install Tools
Make sure the following are installed:
Docker
Minikube
kubectl

You can check by running:
docker --version
minikube version
kubectl version --client

Step 2: Start Minikube
Start your local Kubernetes cluster:
minikube start
Check the cluster status:
minikube status

Step 3: Create a Deployment YAML
Example: Nginx Deployment (nginx-deployment.yaml)
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
spec:
  replicas: 2
  selector:
    matchLabels:
      app: nginx
  template:
    metadata:
      labels:
        app: nginx
    spec:
      containers:
      - name: nginx
        image: nginx:latest
        ports:
        - containerPort: 80

Apply the deployment:
kubectl apply -f nginx-deployment.yaml

Step 4: Expose the Deployment
Create a service (nginx-service.yaml):
apiVersion: v1
kind: Service
metadata:
  name: nginx-service
spec:
  type: NodePort
  selector:
    app: nginx
  ports:
    - port: 80
      targetPort: 80
      nodePort: 30001

Apply the service:
kubectl apply -f nginx-service.yaml

Step 5: Verify Deployment
kubectl get pods
kubectl get deployments
kubectl get services

Access the app:
minikube service nginx-service

Step 6: Take Screenshots
Take screenshots of the following:
kubectl get pods
kubectl get services
The browser showing the Nginx welcome page

Step 7: Cleanup
kubectl delete -f nginx-service.yaml
kubectl delete -f nginx-deployment.yaml
minikube stop

Deliverables:
nginx-deployment.yaml
nginx-service.yaml
Screenshots:
Pods list
Services list
Browser showing Nginx welcome page

I have created a zip file containing the necessary YAML files and a template for screenshots. You can download it.

