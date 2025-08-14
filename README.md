# Taski-Docker

A Dockerized version of the Taski task-planning application—a full-stack web app featuring a React frontend, a Django REST backend, PostgreSQL, an Nginx reverse proxy, and Gunicorn.

## Table of Contents

- [Overview](#overview)  
- [Features](#features)  
- [Architecture](#architecture)  
- [Getting Started](#getting-started)  
  - [Prerequisites](#prerequisites)  
  - [Running with Docker Compose (Development)](#running-with-docker-compose-development)  
  - [Production Deployment](#production-deployment)  
- [Configuration](#configuration)  
- [License](#license)  
- [Contributing](#contributing)  
- [Author](#author)

---

## Overview

Taski is an organizer app that allows users to create, update, and manage tasks—marking them as completed or pending. This Docker-based version simplifies deployment and environment setup via containers.

## Features

- Fully containerized backend and frontend using Docker  
- API built with Django and Django REST Framework  
- Modern frontend with React SPA  
- PostgreSQL database management  
- Gunicorn application server  
- Nginx for reverse proxy and static file serving  
- Streamlined with Docker Compose for easy orchestration  

## Architecture

[User] ←→ Nginx ←→ React Frontend (SPA)
↓
Gunicorn ←→ Django REST API ←→ PostgreSQL


Containers:

- **frontend** (React SPA)  
- **backend** (Django + REST API served by Gunicorn)  
- **db** (PostgreSQL)  
- **nginx** (Reverse proxy / static files)  

## Getting Started

### Prerequisites

- Docker  
- Docker Compose  

### Running with Docker Compose (Development)

1. Clone the repository:
   ```bash
   git clone https://github.com/salahamran/taski-docker.git
   cd taski-docker
   ```

2. Build and start containers:
```bash
docker-compose up --build
```
3. Access the application:
```bash
    - Frontend: http://localhost:3000

    - API: http://localhost:8000/api/
```
4. Stop services with Ctrl+C, or run:
```bash
    docker-compose down
```
5. Production Deployment
```bash
docker-compose -f docker-compose.production.yml up -d --build
```

Ensure environment variables are securely configured (e.g., in .env.production), and that PostgreSQL volumes and Nginx settings align with your production environment.


### Configuration

Customize these configurations:

Environment Variables:

    DJANGO_SETTINGS_MODULE, DATABASE_URL, SECRET_KEY, etc.

Ports: Default ports are 3000 (frontend), 8000 (backend), and 80 (Nginx). Change as needed.

Static Files: The React build outputs and Django static files are managed by Nginx. Modify Nginx config if structure changes.

Volumes: Persisting data (e.g., for PostgreSQL) requires appropriate Docker volumes.


### License

This project is licensed under the MIT License. See the LICENSE file for details.


### Author

Forked and maintained by salahamran. Original project by yandex-praktikum.