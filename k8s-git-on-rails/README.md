# Kubernetes Git-on-Rails

This is a simple example of "Kubernetes Git-on-Rail" Config Sync repository structure. 

It contains main resource definitions to illustrate the commonly used Config Sync repository structure.

The example doesn't contain and deploy any Kubernetes workloads and only illustrates the structure and can be used as Fleet Package deployment directly:

## Setup

### Fork and clone this repo

1. Fork this repo to your account

1. In your terminal, clone this repo locally. 

      ```console
      $ git clone https://github.com/<GITHUB_USERNAME>/anthos-config-management-samples.git
      $ cd anthos-config-management-samples/k8s-git-on-rails/
      ```

### Sync ACM Operator

The cluster's ACM Operator must be configured to point to this directory.

1. Update [setup/hello-namespace/config-management.yaml](setup/hello-namespace/config-management.yaml) to include your cluster name and git username.

1. Apply the sync config to your cluster

    ```console
    $ kubectl apply -f setup/hello-namespace/config-management.yaml
    ```

1. Confirm the sync was successful with `nomos status`

    ```console
    $ nomos status
    Connecting to clusters...
    Context                                 Status           Last Synced Token
    -------                                 ------           -----------------
    my-acm-cluster-context                  SYNCED           <some commit hash>
    ```

## Config Overview

```console
config-root/
├── README.md
├── system/
├── clusterregistry/
├── cluster/
└── namespaces/ # configs that are scoped to namespaces
    └── hello
        └── namespace.yaml # defines a namespace named "hello-namespace"
```
