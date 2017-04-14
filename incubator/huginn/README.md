# Huginn

[Huginn](https://github.com/cantino/huginn/) Huginn is a system for building agents that perform automated tasks for you online. They can read the web, watch for events, and take actions on your behalf. Huginn's Agents create and consume events, propagating them along a directed graph. Think of it as a hackable Yahoo! Pipes plus IFTTT on your own server. You always know who has your data. You do.

## TL;DR;

```console
$ helm install incubator/huginn
```

## Introduction

This chart bootstraps a [Huginn](https://github.com/cantino/huginn/) deployment on a [Kubernetes](http://kubernetes.io) cluster using the [Helm](https://helm.sh) package manager.


## Prerequisites

- Kubernetes 1.4+ with Beta APIs enabled
- PV provisioner support in the underlying infrastructure

## Installing the Chart

To install the chart with the release name `my-release`:

```console
$ helm install --name my-release incubator/huginn
```

The command deploys Huginn.js on the Kubernetes cluster in the default configuration. The [configuration](#configuration) section lists the parameters that can be configured during installation. Also includes a MySQL install out of the box.


> **Tip**: List all releases using `helm list`

## Uninstalling the Chart

To uninstall/delete the `my-release` deployment:

```console
$ helm delete my-release
```

The command removes all the Kubernetes components associated with the chart and deletes the release.

## Configuration

The following tables lists the configurable parameters of the Huginn chart and their default values.

|           Parameter           |             Description             |                        Default                        |
|-------------------------------|-------------------------------------|-------------------------------------------------------|
| `imagePullPolicy`             | Image pull policy                   | `IfNotPresent`                                        |
| `serviceType`                 | Kubernetes Service type             | `NodePort`                                        |
| `resources`                   | CPU/Memory resource requests/limits | Memory: `512Mi`, CPU: `300m`                          |

The above parameters map to the env variables defined in [bitnami/huginn](http://github.com/bitnami/bitnami-docker-huginn). For more information please refer to the [bitnami/huginn](http://github.com/bitnami/bitnami-docker-huginn) image documentation.

Specify each parameter using the `--set key=value[,key=value]` argument to `helm install`. For example,

```console
$ helm install --name my-release \
  --set repository=https://github.com/jbianquetti-nami/simple-huginn-app.git,mariadb.mariadbRootPassword=secretpassword \
    incubator/huginn
```

Alternatively, a YAML file that specifies the values for the above parameters can be provided while installing the chart. For example,

```console
$ helm install --name my-release -f values.yaml incubator/huginn
```

> **Tip**: You can use the default [values.yaml](values.yaml)

## Persistence

The [Huginn](https://github.com/cantino/huginn/) image stores the Huginn application and configurations at the `/app`  path of the container.

Persistent Volume Claims are used to keep the data across deployments. This is known to work in GCE, AWS, and minikube.
See the [Configuration](#configuration) section to configure the PVC or to disable persistence.
