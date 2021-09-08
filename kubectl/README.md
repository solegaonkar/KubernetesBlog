# kubectl commands
Kubernetes comes with a simple command line interface - the kubectl. It is very powerful and we can do almost anything with the cluster. 

The kubectl syntax is simple. 
```
kubectl <action> <optional parameters> <target> <optional parameters>
```

The action could be get, describe, create, delete, edit, apply, exec.. The target could be the the pod, deployment, service, container, ...

## Get
We can use the kubectl get to fetch the list of nodes, pods, etc. It just pulls a list and shows in the STDOUT.

```
kubectl get nodes
```
```
kubectl get pod
```
```
kubectl get services
```
```
kubectl get deployment
```
```
kubectl get replicaset
```

## Edit
It is highly discouraged. But if required, we can directly edit the deployment YAML on the cluster. But it is not advisable. If we do this, we will soon get into an inconsistency where we don't know what is deployed. It is best to update the YAML file in the version control and then push it on the cluster.
```
kubectl edit deployment nginx-depl
```
Similarly we can directly create a new deployment on command line.
```
kubectl create deployment nginx-depl --image=nginx
```
This is the right way to do it.
```
kubectl apply -f nginx-deployment.yaml
```

## Logs
We can print out the logs of the running pod.
```
kubectl logs {pod-name}
```

## Exec
We can also peep into the pod. Just get into its linux shell and see how the world appears in there. This is very useful for debugging. 
```
kubectl exec -it {pod-name} -- bin/bash
```

