## Setting up Docker with Multiple Nodes on Windows

This guide will walk you through the process of setting up Docker with multiple nodes on a Windows machine.

### Prerequisites
- Windows 10 or later
- Docker Desktop installed

### Steps

1. **Install Docker Desktop**
   - Download and install the latest version of Docker Desktop from the official website: [https://www.docker.com/products/docker-desktop](https://www.docker.com/products/docker-desktop)
   - Follow the installation instructions provided by the Docker Desktop installer.

2. **Enable Kubernetes**
   - Open the Docker Desktop application.
   - Click on the "Settings" or "Preferences" menu.
   - Navigate to the "Kubernetes" tab and ensure that the "Enable Kubernetes" option is checked.
   - Click "Apply & Restart" to save the changes.

3. **Create a Kubernetes Cluster**
   - Open a PowerShell or Command Prompt window.
   - Run the following command to create a Kubernetes cluster with multiple nodes:
     ```
     kubectl create clusterrolebinding user-admin-binding --clusterrole=cluster-admin --user=$(docker info -f '{{.DefaultUsername}}')
     ```
   - This command grants the current user admin privileges on the Kubernetes cluster.

4. **Scale the Kubernetes Cluster**
   - In the same PowerShell or Command Prompt window, run the following command to scale the Kubernetes cluster to 3 nodes:
     ```
     kubectl scale deployment.apps/kubernetes-dashboard -n kubernetes-dashboard --replicas=3
     ```
   - This command scales the Kubernetes dashboard deployment to 3 replicas, effectively creating 3 nodes in the cluster.

5. **Verify the Cluster**
   - Run the following command to list the nodes in the Kubernetes cluster:
     ```
     kubectl get nodes
     ```
   - You should see 3 nodes listed, each with a different name.

That's it! You now have a Docker environment with a Kubernetes cluster consisting of 3 nodes running on your Windows machine.

You can now deploy your Docker containers and services across the multiple nodes in the cluster, taking advantage of the increased resources and scalability.

Remember to consult the Docker and Kubernetes documentation for more advanced configuration and deployment options.
