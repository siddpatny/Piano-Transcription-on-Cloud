# piano-transcription-on-cloud

# deploy a new image to kubernetes
```
export PROJECT_ID={your-project-id}
docker build -t gcr.io/${PROJECT_ID}/transcription:<a new tag> .
docker push gcr.io/piano-transcription-276101/transcription:<a new tag>
kubectl set image deployment/transcribe transcription=gcr.io/${PROJECT_ID}/transcription:<a new tag>

# if you want to delete the service and deploy again
kubectl delete service transcribe
kubectl delete deployment transcribe
kubectl create deployment transcribe --image=gcr.io/${PROJECT_ID}/transcription:<a new tag>
kubectl expose deployment transcribe --type=LoadBalancer --port 80 --target-port 5000

```
# check logs
```
kubectl get pods
kubectl logs <the running pod's name>
```
