## Install cert-manager
    kubectl apply -f https://github.com/cert-manager/cert-manager/releases/download/v1.13.1/cert-manager.yaml

or 

Installing cert-manager
	• It can be installed with a YAML manifest, or with Helm
	• Let's install the cert-manager Helm chart with this one-liner:


      helm install cert-manager cert-manager \
        --repo https://charts.jetstack.io \
        --create-namespace --namespace cert-manager \
        --set installCRDs=true

 
<https://cert-manager.io/docs/installation/kubectl/> 

  


## Install ingress-controller Nginx


    helm upgrade --install ingress-nginx ingress-nginx \
      --repo https://kubernetes.github.io/ingress-nginx \
      --namespace ingress-nginx --create-namespace 
      

  <https://kubernetes.github.io/ingress-nginx/deploy/> 
   
example of ingress resources : 

    kubectl create ingress --namespace dev ingress-fastapi --class=nginx\
    --rule=fastapi.devops-youss.cloudns.ph/*=fastapi-dev:5000

    kubectl create ingress  ingress-demo --class=nginx\
    --rule=demo.yous-devops.cloudns.ph/*=my-dep:80


##  Install Stack Prometheus Grafana


    helm upgrade --install kube-prometheus-stack kube-prometheus-stack \
    --namespace kube-prometheus-stack --create-namespace \
    --repo https://prometheus-community.github.io/helm-charts
    	
     
  
      kubectl get all --namespace kube-prometheus-stack

     

Exposing Grafana
	Let's create an Ingress for Grafana
 
       kubectl create ingress --namespace kube-prometheus-stack grafana \
       --rule=grafana.cloudnative.party/*=kube-prometheus-stack-grafana:80
        
        	
      kubectl create ingress --namespace kube-prometheus-stack grafana \
      --rule=grafana.cloudnative.party/*=kube-prometheus-stack-grafana:80







