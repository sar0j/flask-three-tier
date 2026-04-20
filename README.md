# Flask Three-Tier AWS Architecture

A production-style three-tier web application deployed on AWS using modern DevOps practices.

## Architecture
Internet → ALB → ECS Fargate (Flask) → RDS MySQL
## Tech Stack
- **App:** Python Flask REST API
- **Container:** Docker + Amazon ECR
- **Orchestration:** Amazon ECS Fargate
- **Database:** Amazon RDS MySQL
- **Infrastructure:** Terraform (modular)
- **CI/CD:** GitHub Actions
- **Networking:** VPC, ALB, NAT Gateway, Security Groups

## API Endpoints
| Method | Endpoint | Description |
|--------|----------|-------------|
| GET | `/` | Home page |
| GET | `/health` | Health check |
| GET | `/users` | List all users |
| POST | `/users` | Create a user |
| DELETE | `/users/:id` | Delete a user |

## CI/CD Pipeline
Every push to `main` automatically:
1. Runs tests
2. Builds Docker image
3. Pushes to ECR
4. Deploys to ECS (zero downtime)

## Infrastructure
Provisioned with Terraform modules:
- `modules/networking` — VPC, subnets, IGW, NAT
- `modules/security` — Security groups
- `modules/compute` — ALB, ASG, Bastion
- `modules/database` — RDS MySQL
- `modules/storage` — S3, IAM
- `modules/ecs` — ECS cluster, service, task definition
