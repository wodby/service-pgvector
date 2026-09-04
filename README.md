# PostgreSQL (pgvector) service for Kubernetes on Wodby

Run PostgreSQL (pgvector) as a database for Kubernetes applications managed by
Wodby.

This repository defines the Wodby service manifests and operational
configuration for PostgreSQL (pgvector).

- [Browse Wodby services](https://wodby.com/services)
- [Wodby service documentation](https://wodby.com/docs/2.0/services/)
- [Service manifest reference](https://wodby.com/docs/2.0/services/template/)

## Wodby stacks using this service

- [Chatwoot application stack](https://github.com/wodby/stack-chatwoot)

## Service overview

| Property | Manifest configuration |
| --- | --- |
| Service name | `pgvector` |
| Type | Database |
| Inherits from | `postgres` with version constraint `^1.1.0` |
| Versions | `18` by default |
| Workloads | Inherited or externally managed |
| Containers | Inherited or chart-managed |
| Endpoints | None |
| Service links | None |
| Application build | Not buildable from application source |

## Use this service

Use this service through [Chatwoot application stack](https://github.com/wodby/stack-chatwoot), or reference `pgvector` from a
custom Wodby stack.

A service is a reusable component and does not deploy by itself. The stack
defines its links, settings, versions, resources, and relationship to the rest
of the application.

## pgvector lifecycle

The image bundles pgvector and defaults `POSTGRES_DB_EXTENSIONS` to `vector`.
Configured extensions are installed in every application database created
through Wodby, while imports and backups retain the standard PostgreSQL
behavior.

## Maintain a custom version

1. Fork this repository.
2. Edit the service manifest and referenced files.
3. Import the repository as a [Git-backed service](https://wodby.com/docs/2.0/services/create/#create-a-git-backed-service).
4. Reference the service from a stack manifest.

Keep service, workload, container, endpoint, link, volume, config, and
derivative names stable unless dependent stacks and app-level overrides are
updated at the same time.

Validate the manifests with:

```bash
wodby service validate-manifest service.yml --org <org-id>
```

See the [service manifest reference](https://wodby.com/docs/2.0/services/template/) and the [managed services index](https://github.com/wodby/services).
