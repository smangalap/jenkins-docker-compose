# ISEC6000 Assessment 2 – Jenkins Docker Compose

This repository contains the Docker Compose configuration used to run Jenkins and Docker-in-Docker (DinD) for ISEC6000 Assessment 2.

## Main Services

- **Jenkins** – runs the CI/CD pipeline.
- **Docker-in-Docker (DinD)** – provides the Docker daemon used by Jenkins to build and push Docker images.

## Repository Structure

```text
jenkins-docker-compose/
├── docker-compose.yml
├── docs
├── README.md
└── jenkins/
    └── Dockerfile
```

## Start the Environment

```bash
docker compose up -d
```

Check the containers:

```bash
docker compose ps
```

## Access Jenkins

```text
http://localhost:8080
```

## Verify Docker Connection

```bash
docker exec jenkins docker version
```

If both Docker **Client** and **Server** information are displayed, Jenkins is successfully connected to the DinD service.

## Security

- Jenkins runs as the non-root `jenkins` user.
- TLS is used between Jenkins and DinD.
- Jenkins web access is restricted to `127.0.0.1:8080`.
- A private Docker network is used.
- Docker volumes keep Jenkins and Docker data persistent.
- Docker Hub credentials are stored in Jenkins Credentials.

## Useful Commands

Start:

```bash
docker compose up -d
```

Stop:

```bash
docker compose down
```

Restart:

```bash
docker compose restart
```

View Jenkins logs:

```bash
docker compose logs jenkins
```


