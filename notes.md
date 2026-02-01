# Cloud Native Computing Foundation (CNCF)


### Study
Study Hours (14):
2 Friday -> 3 hours
7 days -> 1.5

### Exam
- Better to take an exam in person than online 
- Passing score above 75% grade 
- 60 questions about 15 questions can be wrong 
- Duration exam 90min (around 1.5 min for each question)
- 2 Attempts are allowed to pass
- It is valid for 3 years
- Registration:
  - https://training.linuxfoundation.org/certification/kubernetes-cloud-native-associate/
  - Ask google AI to give you active coupon codes for KCNA exam in Netherlands
- Here is Exam guide: https://github.com/cncf/curriculum


Sandsbox or hands on: 

Learning: https://www.exampro.co
Roadmap: 
 - Kubernetes: KCNA -> CKAD (this is my goal)
 - Programming: Symfony, Node
 - Associate-level Cloud Certificate: AWS or GCP
 - IT Networking Certificate: Cisco CCNA or CompTIA Network+
 - Linux Certificate: CompTIA Linux+, Redhat, Linux Foundation
 - Soft skill: dutch or english

[Documentation](https://kubernetes.io/docs/concepts/overview/components/)


## Kubernetes and Cloud Native Associate (CNCF -> KCNA)
- Cloud native technology landscape
- Core kubernetes components
- CNCF Projects and cloud native tooling
- Security, Deployment and Monitoring

## Exam domains:
- Kubernetes Fundamentals
- Container Orchestration
- Container Native Architecture
- Cloud Native Observability
- Cloud Native Application Delivery 


# What is Cloud Native
- An architectural approach
- Focused on application workloads that will be portable, modular and isolated
- between different cloud deployment models and cloud service provider (CSP)
- it has 4 principles:
  - Microservices
  - Containerization
  - Continuous Delivery
  - DevOps

Cloud-Native will mean technologies like Kubernetes and CNCF projects that are both distributed and are agnostic to
any Cloud Service Provider (CSPs)

Cloud Native vs Cloud Service Providers:
- CSP
  - A collection of cloud services 
  - Strong application integration and synergies between services 
  - Utilizing metered billing 
  - Under a single unified API
- Cloud-Native is a workload, application, or system, that is designed to run on cloud services (all actually needs is a compute)

> Note: all services CSP provides basically is just a computing (dedicated server) but they intentionally try to limit you
in order to encourage you to use their managed services that have exclusive integrations with other services.

# Cloud Native Shared Responsibility Model

There are three type of Responsibility models:
- Traditional IT: Responsibilities split across multiple specialized teams
  - App Team → Applications, Runtime 
  - Data Team → Data 
  - Middleware Team → Middleware 
  - Infrastructure Team → OS, Virtualization, Servers, Storage 
  - Network Team → Networking
- Hybrid IT: Teams begin blending responsibilities with DevOps practices.
  - DevOps Team
  - Network Team
- Cloud Native IT: Shared responsibility across cross-functional teams (Code as Infrastructure)
  - GitOps:
    - Developers → Applications, Data, Runtime 
    - Platform Engineers / Tiger Teams → Middleware, OS 
    - Site Reliability Engineers (SREs) → Infrastructure & Operations 
    - Security Engineers → Security controls 
    - Network Engineers → Networking

# Cloud Responsibility Evolution
- On Premise → IaaS → PaaS → CaaS → FaaS 
- Direction:
  - Reduced vendor lock-in risk 
  - Lower innovation cost 
  - Faster time to market

---

- The Linux Foundation (LF) is a non-profit technology consortium
  - founded in 2000 
  - as a merger between Open Source Development Labs and the Free Standards Group
  - to standardize Linux, support its growth and promote its commercial adoption.

https://www.linuxfoundation.org/
https://www.linuxfoundation.org/projects

---

- Cloud Native Computing Foundation (CNCF)
  - is a Linux Foundation project (by project we mean organization)
  - that was founded in 2015 to help advance container technology.
  - operates as an independent organization from its parent organization (LF)
  - has its own board members 
  - has its own global tech conference called: CloudNativeCon + KubeCon 
  - has its own cloud native certifications
  - has its own collection of projects:
    - Kubernetes 
    - Prometheus 
    - Etcd 
    - ContainerD
    - ...

https://www.cncf.io/
https://www.cncf.io/projects/
---

# Cloud Native Landscape

https://landscape.cncf.io/

---

# Cloud Native Trail Map

The Cloud Native Trail Map is a recommended **steps to adopting Cloud-Native** architecture (build, orchestrate and deploy app)

1) Containerization 
2) Continuous Integration and Deployment (CI/CD)
3) Orchestration and Application Definition 
4) Observability and Analysis 
5) Service Proxy, Discovery and Mesh 
6) Networking Policy, and Security 
7) Distributed Databases and Storage 
8) Streaming and Messaging 
9) Container Registry and Runtime 
10) Software Distribution

PNG -> https://github.com/cncf/trailmap

---

# VMs vs Containers

- Virtual Machines (VMs):
  - do not make the best use of space
  - Apps are not isolated which could cause config conflicts, security problems or resource hogging.

- Containers:
  - allow you to run multiple apps which are virtually isolated from each other.

[Image](images/vms-vs-containers.png)

---

# What are Microservices

- Monolithic Architecture (everything on one machine)
  - One app which is responsible for everything 
  - Functionality is tightly coupled 
- Microservices Architecture (you might use CSP services separately or spin up your container on cluster in cloud native)
  - Multiple apps are each responsible for one thing 
  - Functionality is isolated and stateless
  - Easily can be removed, added or managed as a separate component
  - Only trade off is having more effort on setting up communications between these apps

[Image](images/monolithic-vs-microservice.png)

---

# Kubernetes
- Kubernetes is 
  - an open-source container orchestration system
  - for automating deployment, scaling, and management of containers. 
  - Originally created by Google and now maintained by the CNCF as a CNCF Project 
  - Kubernetes is commonly called K8s (The 8 represent the remaining letters “ubernete”)
  - A unique component of Kubernetes are Pods. A pod is 
    - a group of one or more containers
    - with shared storage, network resources, and other shared settings.

**The advantage** of `Kubernetes` over `Docker` is the ability to run “container apps” distributed across multiple VMs (we call VMs -> nodes)

Kubernetes is ideally for `micro-service` architectures where a company has tens to hundreds of services they need to manage

[Image](images/kubernetes.png)

---

# Kubernetes Components Overview

- Cluster
  A logical grouping of all Kubernetes components.
  Encompasses `control plane` and `worker nodes`.
  
- Namespace
  Logical grouping of components within a cluster.
  Used to isolate workloads and manage resources efficiently.
  
- Node
  A virtual, serverless container or physical machine hosting workloads.
  `Control Plane Node`: Manages cluster state or worker nodes.
  `Worker Node`: Runs applications and workloads.
  
- Pod
  The smallest deployable unit in Kubernetes.
  An abstraction over a container.
  Each pod runs one or more containers that share resources and networking.
  
- Service
  Provides a stable IP and DNS name for a set of pods. because pods constantly can be killed and this will assign a new IP this is why service is there to let us route to pods
  Ensures connectivity even if pods restart.
  Can act as a load balancer.
  
- Ingress
  Manages HTTP/S routing to services from outside the cluster.
  Can include TLS termination.
  
- API Server
  Entry point for all K8s commands via `kubectl` or HTTPs API.
  Handles communication between components.
  
- Kubelet
  Agent running on each node.
  Ensures containers are running as defined in Pod specs.
  Communicates with API Server.
  
- Kubectl
  Command Line Interface (CLI) for managing the cluster.
  Sends commands to the API Server.
  
- Cloud Controller Manager
  Connects Kubernetes to cloud provider APIs (e.g., AWS, Azure, GCP).
  
- Controller Manager
  Watches cluster state and reconciles desired vs. current state.
  Manages controllers like Node, Replication, and Endpoint controllers.
  
- Scheduler
  Assigns pods to nodes based on available resources and constraints.
  
- Kube Proxy
  Maintains network rules on nodes for routing and load balancing of pods.
  
- Network Policy
  Acts as a virtual firewall at pod or namespace level.
  
- ConfigMap
  Stores non-confidential configuration data in key-value pairs.
  Decouples configuration from container images.
  
- Secret
  Stores sensitive data (e.g., passwords, tokens, keys).
  Base64-encoded but should be encrypted in production.
  
- Volumes
  Provides persistent storage for pods.
  Can be local or remote (e.g., cloud storage).
  
- StatefulSet
  Manages stateful applications requiring stable IDs and storage.
  Used for databases or apps needing ordered deployment.
  
- ReplicaSet
  Ensures a specified number of pod replicas are running.
  Provides high availability and fault tolerance.
  
- Deployment
  Defines blueprints for pods.
  Automates rolling updates and rollbacks.

---

# Manifest Files in Kubernetes
- Manifest (not technical description)
  - A Manifest file is a document that is commonly used for customs to list the contents of cargo, or passengers. Its an itemized list of things.

- Manifest File (in the context of Kubernetes)
  - A Manifest file is a generalized name for any Kubernetes Configuration File that define the configuration of various K8s components. 
  - These are all Manifest files with specific purposes:
    - Deployment File 
    - PodSpec File 
    - Network Policy File 
  - Manifest Files can be written in either:
    - YAML 
    - JSON 
- A manifest can contain multiple K8s component definitions/configurations. 
- In YAML you can see the three hyphens `---` is used to defined multiple components.
- `kubectl apply` or `kubectl apply -f resource.yml` command is generally used to deploy manifest files 
- Resource Configuration file is sometimes used to describe multiple resources in a manifest.

[kubectl](https://kubectl.docs.kubernetes.io/references/kubectl/)

---

# Control Plane vs Worker Nodes
- Control Plane Node
- Manages processes like scheduling, restarting nodes, maintaining the overall state of the cluster (kube-system namespace)
  - API Server – the backbone of communication 
  - Scheduler – determines where to start a pod on worker node
  - Controller Manager – detect state changes (if pod crashes, restart it)
  - etcd – A Key/Value Store that stores the state of the cluster
  - Cloud Control Manager (optional) – Integrates with the cloud provider

- Worker Node: 
  - Does the work of running your app in pods and containers 
  - Components:
    - Kubelet 
    - Kube Proxy 
    - Container Runtime 
    - Pods and Containers

[Image](images/kubernetes-components.png)

Core DNS (Service Discovery): When you have an incoming traffic (typing the website url) it will reach out CoreDNS then
it goes to kube proxy then look up in iptables to find which pod/container the application is need to be reached.

[Image](images/worker-node.png)

---

# Pods
- Pods are the smallest unit in Kubernetes (btw container should be the smallest but not in KCNA). 
- Pods abstract away the container layer so you can directly interact with the Kubernetes Layer. 
- A Pod is intended to run one application in multiple containers 
  - Database Pod, Job Pod, Frontend App Pod, Backend App Pod 
  - You can run multiple apps in a pod but those containers will tightly dependent. (not common)
- Each Pod gets its own private IP address 
  - Containers will run on different ports 
  - Containers can talk to each other via localhost
- Each Pod can have a shared storage volume attached. 
  - All containers will share the same volume
- When the last remaining container dies (maybe crashes) in a pod so does the pod 
  - When a replacement pod is created, the pod will have an IP address will be assigned. 
    - IP addresses are Ephemeral, (temporary) for pods, they don’t by default persist.
- Get pods and show their IP addresses

`kubectl get pod -o wide`
`kubectl get pods -o wide`

[Image](./images/pods.png)

---

# API Server
- The core of the Kubernetes control plane is the API server. 
- The API server exposes an HTTP API that lets end-users, different parts of your cluster, and external components communicate with one another. 
- The Kubernetes API lets you query and manipulates the state of API objects in Kubernetes (for example: Pods, Namespaces, ConfigMaps, and Events). 
- The API server is a component of the Kubernetes control plane that exposes the Kubernetes API. The API server is the front end for the Kubernetes control plane. 
- The main implementation of a Kubernetes API server is kube-apiserver. 
- kube-apiserver is designed to scale horizontally—that is, it scales by deploying more instances. 
- You can run several instances of kube-apiserver and balance traffic between those instances. 
- Everything has to go through the API Server. 
- You can interact with the API Server in three ways:
  - UI*
  - API 
  - CLI KubeCTL

[kube-apiserver](https://kubernetes.io/docs/reference/command-line-tools-reference/kube-apiserver/)
[The Kubernetes API](https://kubernetes.io/docs/concepts/overview/kubernetes-api/)

---

# Deployment
- A Deployment provides declarative updates for Pods and ReplicaSets. 
- A Deployment Controller changes the actual state to the desired state at a controlled rate.
  - The default deployment controller is limited 
  - The default Deployment Controller can be swapped out for other deployments tools eg:
    - Argo CD, Flux, Jenkin X…..
- A Deployment define the desired state of ReplicaSets and Pods. 
- A deployment will always create and manage a ReplicaSet. 
- A ReplicaSet will manage replicas of pod.

[Image](./images/deployment.png)

[Deployment](https://kubernetes.io/docs/concepts/workloads/controllers/deployment/)
[Kubernetes: Deployment Strategies types, and Argo Rollouts](https://rtfm.co.ua/en/kubernetes-deployment-strategies-types-and-argo-rollouts/)

---

# Replica Sets


---

# Stateful vs Stateless

---

# Stateful Sets

Need to be read more about it with an example

---

# Namespaces

`kubectl get namespace`
`kubectl create namespace <THE NAME>`
 
---
 
# In-Tree vs Out-Tree


---

# Endpoints and Endpoint Slices

`kubectl get endpoints`

---


# Jobs and Cron Jobs


---

# Kubernetes Dashboard

---

# Selectors

`kubectl get pods --show-labels`
`kubectl label pods apache-web owner=devops`

---

## Recommended Labels

---

## Selecting Labels

`kubectl get pods --selector env=development`
`kubectl get pods -l env=development`

---

##  Annotations
 
---

# Kubelet

---

## PodSpecFile

---

## gRPC 

---

# KubeCTL 

---

# Distributions

## Minikube

---

## K3s & K3d

---

## Kind

---

## MicroK8s

---
