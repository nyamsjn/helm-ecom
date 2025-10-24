# Managing NGINX with Helm

## Prerequisites

* Helm installed on your system.
* A running Kubernetes cluster.
* kubectl configured to interact with the cluster.

---

### 1. Installing NGINX using Helm

To deploy NGINX, we will use the Bitnami Helm chart.

1. **Add the Bitnami repository:**

   ```bash
   helm repo add bitnami https://charts.bitnami.com/bitnami
   helm repo update
   ```

2. **Install the NGINX Helm chart:**

   ```bash
   helm install my-nginx bitnami/nginx
   ```

3. **Verify the installation:**

   ```bash
   helm list
   kubectl get pods
   ```

---

### Customize during Installation

* To see available values for customization, run:

  ```bash
  helm show values bitnami/nginx
  ```
* To preview the manifest without deploying:

  ```bash
  helm template my-nginx bitnami/nginx
  ```

---

### 2. Upgrading NGINX using Helm

To upgrade the NGINX release, we can overwrite the values using --set option on CLI or you can create a custom value yaml file.

For Custom value yaml file, you need to create first then overwrite parameter.

* One wait to create custom value yaml file. The command below will create custom-nginx-values.yaml with all default values of NGINX

   ```bash
   helm show values bitnami/nginx > custom-nginx-values.yaml
   
   ```

1. **Upgrade the release:**

* Using --set option on CLI:

   ```bash
   helm upgrade my-nginx bitnami/nginx --set service.type=NodePort
   ```
* Using custom value yaml file:

   ```bash
   helm upgrade my-nginx bitnami/nginx -f custom-nginx-values.yaml
   
   ```

2. **Check the upgrade status:**

   ```bash
   helm status my-nginx
   ```

---

### 3. Uninstalling NGINX using Helm

To remove the NGINX release from the cluster:

1. **Uninstall the release:**

   ```bash
   helm uninstall my-nginx
   ```

2. **Verify the uninstallation:**

   ```bash
   helm list
   kubectl get pods
   ```

---



