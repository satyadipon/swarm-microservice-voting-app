# Swarm Microservice Voting App

This project is a microservices-based voting application, designed to run on Docker Swarm. It consists of several services: a voting frontend, a results display, a worker, Redis, Postgres, and a visualizer for the Swarm cluster.

## Services

- **vote**: Python web app for voting (ports: 5004)
- **result**: Node.js web app for displaying results (ports: 5003)
- **worker**: .NET worker for processing votes
- **redis**: In-memory data store for vote queue
- **db**: Postgres database for storing results (ports: not exposed)
- **visualizer**: Swarm visualizer UI (ports: 8080)

## Prerequisites

- Docker and Docker Compose (or Docker Swarm)
- [Colima](https://github.com/abiosoft/colima) (if running on macOS without Docker Desktop)

## Usage

### 1. Start Colima (if using Colima)
```sh
colima start --runtime docker
```

### 2. Initialize Docker Swarm (if not already initialized)
```sh
docker swarm init
```

### 3. Create Overlay Network
```sh
docker network create --driver overlay voteapp_net
```

### 4. Deploy the stack
```sh
docker stack deploy -c docker-compose.yml voteapp
```

### 5. Access the app
- Voting frontend: [http://localhost:5004](http://localhost:5004)
- Results: [http://localhost:5003](http://localhost:5003)
- Swarm visualizer: [http://localhost:8080](http://localhost:8080)
