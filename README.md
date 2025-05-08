# EKS Terraform Pipeline 🚀

Provision a secure, production-ready Amazon EKS cluster using Terraform and automate the deployment process with GitHub Actions.

## 📌 Project Overview

This project sets up an AWS Elastic Kubernetes Service (EKS) cluster using Terraform Infrastructure-as-Code and automates the CI/CD workflow with GitHub Actions.

It includes:
- Modular Terraform configuration for scalable infrastructure
- GitHub Actions pipeline for format checks, plan validation, and auto-apply on push
- AWS IAM authentication via GitHub Secrets

## 📁 Folder Structure

.
├── .github
│ └── workflows
│ └── terraform.yml # GitHub Actions pipeline
├── .terraform/ # (gitignored) Terraform local cache
├── main.tf # Core infrastructure
├── variables.tf # Input variables
├── outputs.tf # Output values
├── terraform.tfstate # (gitignored) Terraform state
├── terraform.tfstate.backup # (gitignored) Backup state
├── .terraform.lock.hcl # Provider lockfile
└── .gitignore # Exclude unnecessary files

## 🛠️ Setup Instructions

### 1. Clone the repo

git clone https://github.com/<your-username>/eks-terraform-pipeline.git
cd eks-terraform-pipeline

2. Configure AWS Credentials
Add the following secrets to your GitHub repository:

AWS_ACCESS_KEY_ID

AWS_SECRET_ACCESS_KEY

These are used by GitHub Actions to authenticate with AWS.

3. Push to Trigger CI/CD
The GitHub Actions pipeline will:

✅ Format check

✅ Terraform Init

✅ Terraform Plan

✅ Auto-apply on push to main

✅ Result
After the workflow completes, confirm your cluster:

aws eks --region us-east-1 update-kubeconfig --name k8s-demo
kubectl get nodes

🧠 Lessons Learned
EKS provisioning involves multiple AWS dependencies (IAM roles, KMS keys, VPC, etc.)

CI/CD pipelines benefit from format + plan + apply separation

GitHub Secrets + hashicorp/setup-terraform makes remote workflows seamless
