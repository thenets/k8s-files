# Kubernetes Dashboard

## Setup

Follow the instructions at:
https://github.com/kubernetes/dashboard

```bash
# This probably is an old version!
kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v2.0.3/aio/deploy/recommended.yaml
```

## Create a Service Account

You will need to have a Service Account:

```bash
kubectl apply -f serviceaccount-admin.yml
```

## Get the token

```bash
kubectl -n kube-system describe secret $(kubectl -n kube-system get secret | grep admin-dashboard | awk '{print $1}') | grep "token:"
```

## Start the proxy server

```bash
kubectl proxy
```

Now you can access the Kubernetes Dashboard:
- http://localhost:8001/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy/

## Credits

- https://medium.com/@kanrangsan/creating-admin-user-to-access-kubernetes-dashboard-723d6c9764e4
