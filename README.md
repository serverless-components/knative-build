# knative-build

Instantly create and manage Knative build definitions running on top of [Tekton](https://tekton.dev) Pipelines in your Kubernetes cluster with [Serverless Components](https://github.com/serverless/components).

&nbsp;

1. [Install](#1-install)
2. [Create](#2-create)
3. [Configure](#3-configure)
4. [Deploy](#4-deploy)

&nbsp;

### 1. Install

```console
$ npm install -g serverless
```

### 2. Create

Just create a `serverless.yml` file

```console
$ touch serverless.yml
```

Make sure that you have generated your [`Kubeconfig` file](https://rancher.com/docs/rancher/v2.x/en/cluster-admin/kubeconfig/) via `kubectl`.

### 3. Configure

```yml
# serverless.yml
org: acme
app: todo
name: todo-knative-build

component: knative-build@dev

inputs:
  # use one of the following 2 source definitions
  gitUrl: git@acme.com:engineering/accounting-taxes.git#master # supports `git` or `https` URLs
  bucketUrl: http://acme.s3-us-east-1.amazonaws.com/accounting-taxes # AWS S3 or Google Cloud Storage bucket
  dockerfile: '.' # the Dockerfile located within the source code
  context: '.' # the build context located within the source code
  tag: latest # default is `latest`
  registryAddress: 'https://container-registry.acme.com' # default is `'https://index.docker.io/v1'`
  environment: # optional environment variables
    STAGE: prod
```

### 4. Deploy

```console
$ serverless
```

### New to Components?

Checkout the [Serverless Components](https://github.com/serverless/components) repo for more information.
