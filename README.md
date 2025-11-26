# GitOps for Azure and AWS Deployment

## Set up

You should have an active and properly configured Azure or AWS account.

## What I did

I leveraged GitOps principles using Azure(Azure Repos, Azure Pipeline, Azure DevOps, Azure Kubernetes Service) and AWS(IAM, Amazon EKS, Amzon ECR, Amazon CodePipeline, Amazon CodeBuild, Amazon Lambda)

### Azure

```
az login
terraform init
terraform plan -out aksplan
terraform apply -auto-approve aksplan
az aks get-credentials --resource-group aks-k8s-deployments-rg --name aksgitopscluster
kubectl get pods --namespace weather-app-namespace
terraform destroy --auto-approve
```

### AWS

```
aws configure
terraform init
terraform plan -out awsplan
terraform apply -auto-approve awsplan
aws eks --region eu-central-1 update-kubeconfig --name eksgitopscluster
kubectl cluster-info
terraform destroy --auto-approve
```
