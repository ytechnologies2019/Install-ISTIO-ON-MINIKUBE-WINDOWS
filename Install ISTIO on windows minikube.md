1 - Download Istio File for Windows and Extract
https://github.com/istio/istio/releases/download/1.17.1/istio-1.17.1-win.zip
______________________________________________
2 - Istio Working 
cd C:/istio-1.17.1/bin/
_________________________________________________
3 - Add the istioctl client to the PATH:
set PATH=$PWD/istio-${ISTIO_VERSION}/bin:$PATH
___________________________________________________
4 - Verify the Version.
istioctl version
______________________________________________________
5 - Check kubernetes environment meets Istio's platform requirement.
istioctl x precheck
____________________________________________________________________
6 - create profile
istioctl profile list
___________________________________________________________________________
7 - Use demo profile to install Istio
istioctl install --set profile=demo -y
_________________________________________________________________________________
8 -  Check out the resources installed by Istio
kubectl get all,cm,secrets,envoyfilters -n istio-system
______________________________________________________________________________________
9 -  Check out Custom Resource Definitions (CRDs) installed by Istio:
kubectl get crds -n istio-system
______________________________________________________________________________________________
10 - Verify the installation 
istioctl verify-install
____________________________________________________________________________________________________
11 - Install Istio Telemetry Add-ons
kubectl apply -f samples/addons
________________________________________________________________________________________________________
12 - Verify the Pod
kubectl get pods -n istio-system
_____________________________________________________________________________________________________________
13 - Verify the Add-ons
	
	13(i)  kubectl get pods -n istio-system
	
	Enable Prometheus Dashboard
	13(ii) istioctl dashboard prometheus --browser=false --address 0.0.0.0
	
	Enable Grafana Dashboard
	13(iii) istioctl dashboard grafana --browser=false --address 0.0.0.0
	
	Enable the Jaeger Dashboard
	13(iv) istioctl dashboard jaeger --browser=false --address 0.0.0.0
	
	Enable the Kiali Dashboard
	14(v) istioctl dashboard kiali --browser=false --address 0.0.0.0
