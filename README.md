# Cf-security-entitlement-boshrelease

This will deploy a [cf-security-entitlement server](https://github.com/orange-cloudfoundry/cf-security-entitlement) 
collocated to your cloud foundry api. This must be used with cloud foundry deployment available at https://github.com/cloudfoundry/cf-deployment.

## Instructions

1. Apply ops file at [/manifests/operations/cf/enable-cf-security-entitlement.yml](/manifests/operations/cf/enable-cf-security-entitlement.yml) to your deployment
2. Server will be available at `https://cfsecurity.your.system.domain`

Example:
```bash
bosh -e my-env -d cf deploy cf-deployment/cf-deployment.yml \
  -v system_domain=$SYSTEM_DOMAIN \
  -o operations/scale-to-one-az.yml \
  -o operations/use-compiled-releases.yml \
  -o operations/experimental/fast-deploy-with-downtime-and-danger.yml \
  -o cf-security-entitlement/manifests/operations/cf/enable-cf-security-entitlement.yml
```