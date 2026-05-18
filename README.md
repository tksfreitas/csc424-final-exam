# CSC424 Final Exam  Containerization & CI/CD

## DevOps Setup

### Running the stack locally

```bash
docker compose up --build -d
```

Access the application on **port 80**:

- **Frontend:** http://localhost
- **Backend:** http://localhost/api/ping

### Services

- **frontend**  React + Vite app built with Node and served via Nginx as static files
- **backend**  .NET 10 Web API that handles application logic and exposes REST endpoints
- **nginx**  Reverse proxy that routes traffic to the frontend and backend containers. It is the only service exposed to the host on port 80

### CI/CD Pipeline

The GitHub Actions workflow at `.github/workflows/deploy-qa.yml` triggers on every push to `main`. It builds both Docker images, pushes them to GitHub Container Registry (GHCR), SSHs into the QA server, pulls the latest images, and runs `docker compose up -d` to redeploy the stack automatically.
