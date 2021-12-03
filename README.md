# linkerd-flux-test

Example [Flux v2](https://fluxcd.io/) repo to deploy [Linkerd](https://linkerd.io/).

Dependencies:
* [cert-manager](https://cert-manager.io/) - Used to manage TLS CA/certificates/webhooks

## How it works:

By default the `linkerd` command will generate certificates and then install Linkerd via a bundled Helm chart supplying certificate details as Helm values. 

This Flux setup works in a similar manner by having Cert Manager generate various certificates and then Flux deploys a Helm chart using some predefined values, and by taking the certificate data from various secrets that Cert Manage has created.

At a high level, Cert Manager generates a Root CA certificate for Linkerd as well as certificates for Linkerd's various webhooks and rotates the certificates daily.
