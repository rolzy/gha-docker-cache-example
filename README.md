# Caching Docker Images with Github Actions - an example

## Repo Structure
```
.
├── docker
│   └── Dockerfile          # Dockerfile that will build the Docker image
├── .github
│   └── workflows
│       └── main.yaml       # The Github Actions workflow that will run in a pull request
└── README.md

```

## How it works
The Github Workflow triggers within Pull Requests targeted to the `main` branch.
When triggered, the workflow will build a Docker image defined in `docker/Dockerfile` on each commit pushed to the Pull Request.

The [Github Actions cache](https://docs.docker.com/build/cache/backends/gha/) backend is used to store any build results from Docker. This cache will be used in subsequent builds within the pull request. Note that the cache is not used between separate PRs. Therefore, a full build is required for the first commit of a new pull request.
