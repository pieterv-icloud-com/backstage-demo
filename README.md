# backstage-demo

## Links

- [backstage site](backstage.io)

## Installing

[Deploying with Helm](https://backstage.io/docs/deployment/helm)

### Create kind cluster

Check this [article](https://dustinspecker.com/posts/test-ingress-in-kind/)

```bash
kind create cluster --config kind/kind.yaml --name backstage-demo
```

### Install nginx ingress controller

```bash
kubectl apply --filename https://raw.githubusercontent.com/kubernetes/ingress-nginx/master/deploy/static/provider/kind/deploy.yaml
```

```bash
 kubectl delete ValidatingWebhookConfiguration  ingress-nginx-admission
```

### backstage

```bash
cd ..
git clone https://github.com/backstage/backstage.git
cd backstage/contrib/chart/backstage
helm dependency update
helm install --namespace backstage --create-namespace --values ../../../../backstage-demo/backstage-mydomain.yaml backstage .
```