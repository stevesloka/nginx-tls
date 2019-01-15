# nginx-tls

Provides a nginx deployment with TLS via passed in certs:

```
# Generate certs
$ openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout tls.key -out tls.crt -subj "/CN=tls.containersteve.com"

# Create secrets
$ kubectl create secret generic nginxcerts --from-file=tls.crt --from-file=tls.key

# Create configmap
$ kubectl create configmap nginxconfigmap --from-file=config.conf

# Apply to k8s
$ kubectl apply -f deployment.yaml
```
