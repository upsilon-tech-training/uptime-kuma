# Uptime Kuma with Docker Compose

Uptime Kuma is a self-hosted status monitoring solution designed to help you keep track of your services and ensure they are running smoothly. This repository provides a Docker Compose configuration to easily deploy Uptime Kuma in your environment.

## What is Uptime Kuma?

**Uptime Kuma** is an open-source status monitoring solution that allows you to track the availability and performance of your web services. It provides a web-based dashboard where you can monitor the status of your services, get alerts, and view historical uptime data.

### Key Features

- **Service Monitoring**: Continuously checks the availability of your services.
- **Alerting**: Notifies you when a service is down or experiencing issues.
- **Dashboard**: Provides a user-friendly web interface for monitoring.
- **Historical Data**: Allows you to view past uptime and performance metrics.

### Problems Solved

- **Service Downtime**: Detects when your services are down and alerts you.
- **Performance Monitoring**: Keeps track of the performance of your services over time.
- **Easy Setup**: Simplifies the deployment of monitoring tools with Docker.

## Prerequisites

- Docker
- Docker Compose

Ensure that Docker and Docker Compose are installed on your system. You can follow the official Docker [installation guide](https://docs.docker.com/get-docker/) and Docker Compose [installation guide](https://docs.docker.com/compose/install/) if needed.

## Getting Started

### 1. Clone the Repository

First, clone this repository to your local machine

### 2. Configure the Docker Compose File

The `docker-compose.yml` file is pre-configured to get Uptime Kuma running with default settings. Here is the content of the `docker-compose.yml` file:

```yaml
version: '3.9'

services:
  uptime-kuma:
    image: elestio/uptime-kuma
    ports:
      - "9387:3001"
    environment:
      - DB_TYPE=sqlite
      - DB_STORAGE=/app/data/uptime-kuma.db
      - SOFTWARE_VERSION_TAG=latest
      - URL=http://localhost:9387
    volumes:
      - uptime-kuma-data:/app/data
    restart: always
    healthcheck:
      disable: true

volumes:
  uptime-kuma-data:

```

### 3. Start Uptime Kuma

To start Uptime Kuma, run the following command:

```bash
docker-compose up -d
```

