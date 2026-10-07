# CST8915 Lab2: Deploying the Algonquin Pet Store on Azure

- **Student Name**: Tao Lu
- **Student ID**: 41284860
- **Course**: CST8915 Full-stack Cloud-native Development
- **Semester**: Fall 2026

---

# Note

Due to the limitations of my Azure for Students subscription, I was unable to deploy the store-front to Azure Static Web Apps. The store-front is deployed on an Azure VM instead. The backend services (order-service and product-service) are deployed on Azure App Service, and RabbitMQ runs on a dedicated Azure VM as required.

## [Demo Video](https://www.youtube.com/watch?v=YQwEANetz7A)

## Reflection Questions

1. What challenges did you encounter when configuring environment variables in the GitHub Actions workflow?

I did not deploy the frontend using Azure Static Web Apps because of my student subscription. But I did encounter some problems when deploying the frontend using a VM. I first put the 3030 port in the variable, but then the web page showed it could not fetch data. Then I figured out that the product service on App Service actually does not allow traffic on port 3030. So I deleted the port number, just leaving the URL for the product service and order service.

2. How does deploying microservices on Azure Web App Service differ from running them locally?

Last time I deployed the microservices on VMs, for the order service I needed to install Node.js, and I needed to start the program myself. For the product service, I also needed to install the environment and start the program. But on Azure Web App Service, I just need to set the environment variables for them. For the order service, I just gave it the RabbitMQ connection string. I use GitHub to deploy the program, so once I modify my code, it will redeploy and restart automatically. Another difference is that when I deploy locally, I need to specify which port I want to use, but it seems that Azure App Service has a default port for each program.

3. Why is it important to use environment variables for configurations in a cloud environment?

I think it is important because I use GitHub. If I write the configuration directly in the code instead of using environment variables, other people can see it, which is not safe. Besides, if I want to change a value, I don't need to locate it in the code and modify it in the program. I just need to update the environment variable.

## Service Repository

- [order-service](https://github.com/taolucloud2/orderService)
- [product-service](https://github.com/taolucloud2/productservice-python)
- [store-front](https://github.com/taolucloud2/store-front)
