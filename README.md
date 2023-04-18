# Kubernetes WordPress

Deploy a WordPress server on a Kubernetes cluster.

## Prerequisites
- Kubernetes cluster is set up and ready
- Your subdomain points to your Kubernetes cluster
- Kubernetes cluster has a `ClusterIssuer` named `lets-encrypt` set up and ready (may need to be adjusted for your cluster setup)

## Setup
1. Clone this repository and `cd` into it
2. Configure your subdomain in `ingress.yaml` (lines are marked by TODO)
3. May adjust `ClusterIssuer` in `ingress.yaml`
4. Configure passwords in `env-mysql-secret.yaml` (lines are marked by TODO)
5. May adjust `PersistentVolumeClaim` in `db-persistentvolumeclaim.yaml` and `wordpress-persistentvolumeclaim.yaml`. Currently, the default storage class of the cluster is used.
6. Create Kubernetes namespace and create kubernetes configuration
```shell
kubectl create namespace mynamespace
kubectl create -n mynamespace -f ./deploy-kubernetes
```
7. Check if webserver is reachable


## Troubleshooting
In case of webserver is not reachable or errors, check status and logs:
``` bash 
kubectl get all -n mynamespace

kubectl logs -n mynamespace pod/<pod-name>
```