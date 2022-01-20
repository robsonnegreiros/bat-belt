# Kubernetes Cheatsheet

Source converted from PDF: https://www.facebook.com/groups/devopsg/

## Creating Objects:

Create resource

```bash
kubectl apply -f ./<file_name>.yaml
```

Create from multiple files

```bash
kubectl apply -f ./<file_name_1>.yaml -f ./<file_name_2>.yaml
```

Create all files in directory

```bash
kubectl apply -f ./<directory_name>
```

Create from url

```bash
kubectl apply -f https://<url>
```

Create pod

```bash
kubectl run <pod_name> --image <image_name>
```

Create pod, then expose it as service

```bash
kubectl run <pod_name> --image <image_name> --port <port> --expose
```

Create pod yaml file 

```bash
kubectl run <pod_name> --image image_name --dryrun=client -o yaml > <file_name>.yaml
```

Create deployment 

```bash
kubectl create deployment <deployment_name> --image <image_name>
```

Create deployment yaml file

```bash
kubectl create deployment <deployment_name> --image <image_name> --dry-run=client -o yaml > <file_name>.yaml
```

Create service

```bash
kubectl create service <service-type> <service_name> --tcp=<port:target_port>
```

Create service yaml file

```bash
kubectl create service <service-type> <service_name> --tcp=<port:target_port> --dryrun=client -o yaml > <file_name>.yaml
```

Expose service from pod/deployment

```bash
kubectl expose deployment <pod/deployment_name> -- type=<service-type> --port <port> --target-port <target_port>
```

Create config map from key-value

```bash
kubectl create configmap <configmap_name> --fromliteral=<key>:<value> --from-literal=<key>:<value>
```

Create config map from file

```bash
kubectl create configmap <configmap_name> --fromfile=<file_name>
```

Create config map from env file

```bash
kubectl create configmap <configmap_name> --from-envfile=<file_name>
```

Create secret from keyvalue

```bash
kubectl create secret generic <secret_name> --fromliteral=<key>:<value> --from-literal=<key>:<value>
```

Create secret from file

```bash
kubectl create secret generic <secret_name> --fromfile=<file_name>
```

Create job

```bash
kubectl create job <job_name> --image=<image_name>
```

Create job from cronjob

```bash
kubectl create job <job_name> -- from=cronjob/<cronjob-name>
```

Create cronjob

```bash
kubectl create cronjob --image=<image_name> -- schedule='<cron-syntax>' -- <command> <args>
```

## Monitoring Usage Commands:-

Get node cpu and memory utilization

```bash
kubectl top node <node_name>
```

Get pod cpu and memory utilization

```bash
kubectl top pods <pod_name>
```

## Node Commands:-

Describe node

```bash
kubectl describe node <node_name>
```

Get node in yaml

```bash
kubectl get node <node_name> -o yaml
```

Get node

```bash
kubectl get node <node_name>
```

Drain node

```bash
kubectl drain node <node_name>
```

Cordon node

```bash
kubectl cordon node <node_name>
```

Uncordon node

```bash
kubectl uncordon node <node_name>
```

## Pod Commands:-

Get pod

```bash
kubectl get pod <pod_name>
```

Get pod in yaml

```bash
kubectl get pod <pod_name> -o yaml
```

Get pod wide information

```bash
kubectl get pod <pod_name> -o wide
```

Get pod with watch

```bash
kubectl get pod <pod_name> -w
```

Edit pod

```bash
kubectl edit pod <pod_name>
```

Describe pod

```bash
kubectl describe pod <pod_name>
```

Delete pod

```bash
kubectl delete pod <pod_name>
```

Log pod

```bash
kubectl logs pod <pod_name>
```

Tail -f pod

```bash
kubectl logs pod -f <pod_name>
```

Execute into pod

```bash
kubectl exec -it pod <pod_name> /bin/bash
```

Running Temporary Image

```bash
kubectl run <pod_name> --image=curlimages/curl --rm -it -- restart=Never -- curl <destination>
```

## Deployment Commands:-

Get deployment

```bash
kubectl get deployment <deployment_name>
```

Get deployment in yaml

```bash
kubectl get deployment <deployment_name> -o yaml
```

Get deployment wide information

```bash
kubectl get deployment <deployment_name> -o wide
```

Edit deployment

```bash
kubectl edit deployment <deployment_name>
```

Describe deployment

```bash
kubectl describe deployment <deployment_name>
```

Delete deployment

```bash
kubectl delete deployment <deployment_name>
```

Log deployment

```bash
kubectl logs deployment/deployment_name -f
```

Update image

```bash
kubectl set image deployment <deployment_name> <container_name>=<new_image_name>
```

Scale deployment with replicas

```bash
kubectl scale deployment <deployment_name> --replicas <replicas>
```

## Service Commands:-

Get service

```bash
kubectl get service <service>
```

Get service in yaml

```bash
kubectl get service <service> -o yaml
```

Get service wide information

```bash
kubectl get service <service> -o wide
```

Edit service

```bash
kubectl edit service <service>
```

Describe service

```bash
kubectl describe service <service>
```

Delete service

```bash
kubectl delete service <service>
```

## Endpoints Commands:-

Get endpoints

```bash
kubectl get endpoints <endpoints_name>
```

## Ingress Commands:-

Get ingress

```bash
kubectl get ingress
```

Get ingress in yaml

```bash
kubectl get ingress -o yaml
```

Get ingress wide information

```bash
kubectl get ingress -o wide
```

Edit ingress

```bash
kubectl edit ingress <ingress_name>
```

Describe ingress

```bash
kubectl describe ingress <ingress_name>
```

Delete ingress

```bash
kubectl delete ingress <ingress_name>
```

## DaemonSet Commands:-

Get daemonset

```bash
kubectl get daemonset <daemonset_name>
```

Get daemonset in yaml

```bash
kubectl get daemonset <daemonset_name> -o yaml
```

Edit daemonset

```bash
kubectl edit daemonset <daemonset_name>
```

Describe daemonset

```bash
kubectl describe daemonset <daemonset_name>
```

Delete daemonset

```bash
kubectl delete deployment <daemonset_name>
```

## StatefulSet Commands:-

Get statefulset

```bash
kubectl get statefulset <statefulset_name>
```

Get statefulset in yaml

```bash
kubectl get statefulset <statefulset_name> -o yaml
```

Edit statefulset

```bash
kubectl edit statefulset <statefulset_name>
```

Describe statefulset

```bash
kubectl describe statefulset <statefulset_name>
```

Delete statefuleset

```bash
kubectl delete statefulset <statefulset_name>
```

## ConfigMaps Commands:-

Get configmap

```bash
kubectl get configmap <configmap_name>
```

Get configmap in yaml

```bash
kubectl get configmap <configmap_name> -o yaml
```

Edit configmap

```bash
kubectl edit configmap <configmap_name>
```

Describe configmap

```bash
kubectl describe configmap <configmap_name>
```

Delete configmap

```bash
kubectl delete configmap <configmap_name>
```

## Secret Commands:-

Get secret

```bash
kubectl get secret <secret_name>
```

Get secret in yaml

```bash
kubectl get secret <secret_name> -o yaml
```

Edit secret

```bash
kubectl edit secret <secret_name>
```

Describe secret

```bash
kubectl describe secret <secret_name>
```

Delete secret

```bash
kubectl delete secret <secret_name>
```

## Rollout Commands:-

Restart deployment

```bash
kubectl rollout restart deployment <deployment_name>
```

Undo deployment with the latest revision

```bash
kubectl rollout undo deployment <deployment_name>
```

Undo deployment with specified revision

```bash
kubectl rollout undo deployment <deployment_name> --torevision <revision_number>
```

Get all revisions of deployment

```bash
kubectl rollout history deployment <deployment_name>
```

Get specified revision of deployment

```bash
kubectl rollout history deployment <deployment_name> -- revision=<revision_number>
```

## Job Commands:-

Get job

```bash
kubectl get job <job_name>
```

Get job in yaml

```bash
kubectl get job <job_name> -o yaml
```

Edit job in yaml

```bash
kubectl edit job <job_name>
```

Describe job

```bash
kubectl describe job <job_name>
```

Delete job

```bash
kubectl delete job <job_name>
```

## Cronjob Commands:-

Get cronjob

```bash
kubectl get cronjob cronjob_name
```

Get cronjob in yaml

```bash
kubectl get cronjob <cronjob_name> -o yaml
```

Edit cronjob

```bash
kubectl edit cronjob <cronjob_name>
```

Describe cronjob

```bash
kubectl describe cronjob <cronjob_name>
```

Delete cronjob

```bash
kubectl delete cronjob <cronjob_name>
```

## Network Policy Commands:-

Get networkpolicy

```bash
kubectl get networkpolicy <networkpolicy_name>
```

Get networkpolicy in yaml

```bash
kubectl get networkpolicy <networkpolicy_name> -o yaml
```

Get networkpolicy wide information

```bash
kubectl get networkpolicy <networkpolicy_name> -o wide
```

Edit networkpolicy

```bash
kubectl edit networkpolicy <networkpolicy_name>
```

Describe networkpolicy

```bash
kubectl describe networkpolicy <networkpolicy_name>
```

Delete networkpolicy

```bash
kubectl delete networkpolicy <networkpolicy_name>
```

## Labels and Selectors Commands:-

Show labels of node,pod and deployment

```bash
kubectl get <node/pod/deployment> --showlabels
```

Attach labels to <node/pod/deployment>

```bash
kubectl label <node/pod/deployment> <pod_name> <key>=<value>
```

Remove labels from <node/pod/deployment>

```bash
kubectl label <node/pod/deployment> <pod_name> <key>-
```

Select node,pod and deployment by using labels

```bash
kubectl get <node/pod/deployment> -l <key>=<value>
```
