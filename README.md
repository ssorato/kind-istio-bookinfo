# Bookinfo Istio application running on Kind kubernetes cluster

**Notice**: tested on Windows Subsystem for Linux (WSL) 2

## Requirementes

* [Kind Kubernetes cluster](https://kind.sigs.k8s.io/)
* [Task, a task runner / build tool](https://taskfile.dev/)
* [kubectl](https://kubernetes.io/docs/reference/kubectl/kubectl/)

## Install

Set the _Nginx Ingress Controller service load balancer IP_ in the variable `INGRESS_IP` in the [taskfile](Taskfile.yml)

Set the _Metallb IPs range_ in the variable `METALLB_ADDRS` in the [taskfile](Taskfile.yml). Get subnet using the command:

```bash
$ docker network inspect -f '{{.IPAM.Config}}' kind
```

Start the pipeline:

```bash
$ taks
```

Open Bookinfo page at `http://bookinfo.<INGRESS_IP>.nip.io/productpage`

* _Kiali_ is avaliable at `http://addons.<INGRESS_IP>.nip.io/kiali/`
* _Prometheus_ is avaliable at `http://addons.<INGRESS_IP>.nip.io/prometheus/`
* _Grafana_ is avaliable at `http://addons.<INGRESS_IP>.nip.io/grafana/`
* _Jeager_ is avaliable at `http://addons.<INGRESS_IP>.nip.io/jaeger/search`

## Cleanup

```bash
$ taks destroy
```

## References

* [Istio](https://istio.io/latest/docs/)
* [Bookinfo Application](https://istio.io/latest/docs/examples/bookinfo)
* [Istio & Service Mesh - simply explained in 15 mins](https://www.youtube.com/watch?v=16fgzklcF7Y)

