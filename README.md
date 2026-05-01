# 10_DevOps_Kubernetes_Helm
this repository demonstrates deploying Kubernetes cluster using Helm 

- create Kubernetes cluster on Linode cloud platform - https://www.linode.com/
- shared CPUs in selected region, number of worker nodes can be selected.
- download yaml Kubeconfig file Linode platform to local and set permissions to allow only the read priviliges for a user - *chmod 400 <kubeconfigFile>*
- export KUBECONFIG=<pathToKubeconfigFile> to get access to Linode Cluster. All kubectl command will be executed against the Linode Cluster
- install Helm - follow instruction on https://helm.sh/docs/intro/install/]
- add bitnami repository to helm: *helm repo add bitnami https://helm.sh/docs/intro/install/*
- search in the repository: *helm search repo bitnami*
- mongodb can be deployed using helm : *helm install mongodb --values helm-mongodb.yaml bitnami/mongodb*
- mongo-express can be deployed as simle YAML file: *kubectl apply -f helm-mongo-express.yaml*
- add helm chart repository for nginx ingress controller - *helm repo add ingress-nginx https://kubernetes.github.io/ingress-nginx*
- To check the content of repository: *helm search repo ingress-nginx* to show the chart name
- installation of the helm chart from repository, Kubernetes component will be called **nginx-ingress**: *helm install nginx-ingress ingress-nginx/ingress-nginx --set controller*
- on Linode platform a Nodebalancer is dynamically created and Nodebalancer becomes an entrypoint to cluster. 