An operator for deploying HAProxy PROXY Protocol shims

This is useful when you have an ingress which uses PROXY protocol but you want
to also allow its use without PROXY protocol.  A common scenario is when you
have an external load balancer providing client IPs via PROXY protocol but you
want to allow users to connect without the external load balancer,
necessetating the use of another proxy (or shim) to provide PROXY headers to
connections -- this is that "another proxy"

Dependencies:
* template operator from flanksource
  * kubectl apply -f https://github.com/flanksource/template-operator/releases/download/v0.7.1/operator.yml



known bugs:

* if a change is made to the name of a resource, the old resource will not be
  cleaned up until the custom resource itself is cleaned up (there is no
  pruning of intermediate objects, just full garbage collection of child
  objects upon deletion)
