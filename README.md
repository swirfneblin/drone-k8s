[![Build Status](https://975258d0047041.localhost.run/api/badges/swirfneblin/drone-k8s/status.svg?ref=refs/heads/main)](https://975258d0047041.localhost.run/swirfneblin/drone-k8s)

 ## DroneCI kubernetes

Clone project:

  ```sh
  git clone https://github.com/swirfneblin/drone-kubernetes
  cd drone-kubernetes
  ```

### Config

Create custom-values.yaml

  ```yaml
  drone:
    gitClientId: xxxxxxxxxxxxxxxxxxxxx
    gitClientSecret: xxxxxxxxxxxxxxxxxxxxxxxxxx
    sharedsecret: xxxxxxxxxxxxxxxxxxxx
    host: xxxxxxxxxxxxx.localhost.run
    protocol: https

  ```

Install drone server from helm:

  ```sh
  helm install drone --values custom-values.yaml
  ```

Configure port forward and expose public domain:

  ```sh
  kubectl port-forward service/drone 8080:80
  ssh -R 80:localhost:8080 ssh.localhost.run
  ```

### Config CLI

Config drone CLI:

  ```sh
  mkdir -p  ~/.drone-runner-exec/config
  touch ~/.drone-runner-exec/config/config
  ```

### DOCS

Drone: [Install Drone server from GitHub](https://docs.drone.io/server/provider/github/)

