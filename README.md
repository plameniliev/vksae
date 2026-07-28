Usage
---

### Helm Template 

```bash
export VKS_CLUSTER=vks-cluster-102
export VKS_NAMESPACE=demo-7yvl5

argocd app create $VKS_CLUSTER \
  --repo git@github.com:plameniliev/vksae.git \
  --path charts/vks-cluster-chart \
  --revision init \
  --dest-name piliev-supervisor-mgmt \
  --dest-namespace $VKS_NAMESPACE \
  --helm-set name='$ARGOCD_APP_NAME' \
  --helm-set namespace=$VKS_NAMESPACE \
  --helm-set controlPlaneReplicas=1 \
  --helm-set nodePoolReplicas=3 \
  --helm-set vksVersion="v1.34.8---vmware.1-vkr.1" \
  --sync-policy automated \
  --auto-prune
```

### Static

```bash

export VKS_NAMESPACE=play-6t9bt
#export VKS_NAMESPACE=demo-7yvl5

argocd app create namespace-$VKS_NAMESPACE \
  --repo git@github.com:plameniliev/vksae.git \
  --path namespaces/$VKS_NAMESPACE \
  --revision init \
  --dest-name piliev-supervisor-mgmt \
  --dest-namespace $VKS_NAMESPACE \
  --sync-policy automated \
  --auto-prune
```