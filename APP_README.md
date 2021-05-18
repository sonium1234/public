# public

# This file will explain app setup.


STEP 1 
Prepare application / create container images
-> docker-compose up -d
-> docker images
-> docker ps


STEP 2 
Create an Azure Container Registry

-> az group create --name publicResourceGrp --location southuk
-> az acr create --resource-group publicResourceGrp --name publicACR127 --sku Basic

Log in to container registry
-> az acr login --name publicACR127


Tag container image
-> docker images \n
-> az acr list --resource-group publicResourceGrp --query "[].{acrLoginServer:mydemoacr7878.azurecr.io}" --output table
-> docker tag mydemoacr7878.azurecr.io/azuredocs/azure-vote-front:v1 mydemoacr7878.azurecr.io/azure-vote-front:v1
-> docker images

Push images to registry
-> docker push mydemoacr7878.azurecr.io/azure-vote-front:v1

