# cf-k8s-prometheus

This repo contains Prometheus components built with an Ubuntu base image (i.e.
Prometheus server, statsd_exporter, etc) that can be deployed in a [CF for
K8s](https://github.com/cloudfoundry/cf-for-k8s) environment.

### How to Deploy in CF for K8s

When deploying the CF for K8s cluster via the [deploy docs](https://github.com/cloudfoundry/cf-for-k8s/blob/master/docs/deploy.md),
include the `config` directory as shown below:

```
ytt -f ${WORKSPACE}/cf-for-k8s/config -f ${WORKSPACE}/cf-k8s-prometheus/config -f ${TMP_DIR}/cf-values.yml > ${TMP_DIR}/cf-for-k8s-rendered.yml
```

If you wish to deploy Grafana alongside Prometheus:

```
ytt -f ${WORKSPACE}/cf-for-k8s/config -f ${WORKSPACE}/cf-k8s-prometheus/config -f ${WORKSPACE}/cf-k8s-prometheus/experimental/add-grafana.yml -f ${TMP_DIR}/cf-values.yml > ${TMP_DIR}/cf-for-k8s-rendered.yml
```

Default username/password is `admin/admin` and any changes you make in the UI will be blown away on the next deployment update.