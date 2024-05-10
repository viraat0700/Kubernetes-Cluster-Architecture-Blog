# Kubernetes-Cluster-Architecture-Blog

"In this blog, I will explain Kubernetes architecture in the simplest manner possible. We'll go deep into understanding the different components of a Kubernetes cluster and how they actually work. So make sure you read this blog till the end. Let's start.

We begin with creating a cluster. You can create a Kubernetes cluster locally using tools like MiniKube or kubeadm. Optionally, you can also use cloud provider services like EKS in AWS, AKS in Azure, or GKE in Google Cloud to create Kubernetes clusters. Inside this Kubernetes cluster, we have two different types of machines or nodes.

We have a master node, which is responsible for handling everything inside the cluster. Along with the master node, we also have another kind of node known as a worker node. This worker node is responsible for running your application containers inside the Kubernetes cluster.

Now, let's focus on worker nodes and look at the different components inside them. Worker nodes are responsible for running application containers, and they run these application containers inside something known as pods. Pods are the smallest deployable units in the Kubernetes cluster, and a pod can hold one or more containers.

A single worker node can have more than one pod or it can have a single pod as well. These containers are actually running inside an object known as pods. To deploy and manage pods inside the worker node, we have an agent named as kubelet. This kubelet agent is running on all worker nodes and it gets information from the master node to decide where the pod should be running and how to manage it.

Along with this, for a worker machine to create and manage containers, we need to have a Container Runtime Interface (CRI) or a software like Docker. So, the worker machine will also contain a CRI such as Docker.

Other options are Containerd, Rocket, etc., which are supported by Kubernetes as well. Also, to enable communication between these pods or to make these pods or applications accessible to the end-users, we have another networking component in the worker node known as kube-proxy.

Kube-proxy is used for port-to-port communication, load balancing service proxy, and to make your application accessible to the end-users. So, these are the different components inside the worker nodes: kube-proxy for port-to-port communication and exposing your application, CRI to create and delete containers, kubelet an agent that is running on every worker node which gets information from the master node and handles the workloads inside the worker nodes.

Along with this, you can have more add-ons or plugins that you install on your worker nodes, but these are all the important components inside your worker nodes. Now that we have understood the different components inside worker nodes and how they actually work, let's look at the different components inside the Master node.

So, the Master node or control plane has four very important components that are responsible for managing everything inside the cluster. The first component is the kube-api-server. This kube-api-server is like an entry point for everything you do inside the cluster.

So, let's say you are a DevOps engineer and you want to create a new pod, delete a pod, or just get the status, if you want to do anything inside the cluster, you will have to talk to the kube-api-server. You can talk to kube-api-server either by running commands using kubectl command-line tool, using Kubernetes Dashboard, or using SDKs or anything.

So, you will talk to the kube-api-server. Kube-api-server will validate if the request is okay, if the user is authenticated or not, and if it works, then it will get the information from the other components and provide it to the end-user or to the DevOps engineer. So, the API server is like an entry point which validates the request and also authenticates the user.

Next, Master node component is the scheduler. Scheduler is used to assign pods to the worker nodes. Let's say you made a request to the API server to create a new pod. Scheduler is going to check which nodes have enough capacity to launch this new pod. Once the node on which the pod is going to be run is decided by the scheduler, scheduler provides this information to the kube-api-server.

Kube-api-server gives this information to the kubelet running on that particular node and thus, it creates the new pod on the worker node. So, scheduler is used to assign pods on the nodes based on resource capacity or all the manifest files that you have defined for your cluster.

Now, what if there's an issue inside the cluster or one of these pods shows an error or gets deleted? That's when the next Kubernetes Master node component comes into play. So, the next Kubernetes component is the controller manager. Controller manager is used to monitor the entire cluster and it makes sure that everything is as you have defined inside your manifest files.

So, let's say you have said you want to have four pods running. It will make sure that the four pods are running all the time. If that's not the case, it'll tell API server which will recreate the pod following the same procedure with the scheduler first deciding what nodes to create the pods on, then giving the information to the API server, and then kubelet creates it.

Controller manager is used to monitor and make sure everything is working as you want or as you have desired, and it does that by comparing the desired state with the actual state of the cluster. But where is this cluster information or cluster data stored? It is stored inside etcd.

Etcd is a key-value store that stores all the information about the cluster: what applications are running, what pods are running on which nodes, and everything else. One thing to note is etcd can only talk to the kube-api-server.

So, if you want to get any information from etcd, it has to be through the kube-api-server. So, you can see kube-api-server is like a center of communication for every component inside the master node as well as to the kubelet, which is running on the worker node. This is the Kubernetes architecture.

We have Master node and the worker node. Master node is responsible for handling workloads inside the cluster. Worker nodes are actually running the application workloads. Here inside worker node, we have the pods, which are the smallest unit responsible to run the application container. We have kubelet, an agent, which is going to run on all the worker nodes and also responsible to create pods.

Next, we have Container Runtime Interface and we also have kube-proxy for networking and for exposing our application. Inside Master node, we have kube-api-server, which is the entry point and the authentication system for every request that you make. It also exposes a Kubernetes API for the end-user to start using it.

Next component is a scheduler, which is used to assign pods to the nodes. Then we have controller manager that makes sure everything is working as you want or as you have desired. All the cluster information is stored inside etcd.

So, this is a simplified explanation of Kubernetes architecture. I hope this blog was informative. If you have any questions, any doubt, do let me know in the comment section. And for more information, I would recommend checking out my another blog which explains what is Kubernetes and how it actually works. Do check it out. Thank you and have a good day."


