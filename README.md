# Azure Functions Deployment Template

This repository provides a GitHub Actions workflow template to automate the deployment of Python-based Azure Functions. This template is designed for developers looking to streamline their deployment pipeline using GitHub Actions for a smooth continuous deployment experience.

## Workflow Overview

This GitHub Actions workflow deploys a Python Azure Function App to Azure upon each push to the `master` branch. Additionally, the workflow can be triggered manually through the "workflow dispatch" event.

### Key Features
- Automatically sets up Python 3.11 for deployment.
- Installs dependencies listed in `requirements.txt`.
- Logs into Azure using GitHub secrets.
- Deploys directly to the specified Azure Function App.
- Configures necessary settings for Azure Function App runtime.

## Repository Structure

- `.github/workflows/deploy.yml`: The GitHub Actions workflow file.
- `requirements.txt`: List of dependencies to be installed during deployment.
- Azure Function App code files.

---

## Getting Started

### Prerequisites

1. **Azure Subscription**: Ensure you have an Azure account with permissions to deploy resources.
2. **Azure CLI**: [Install the Azure CLI](https://docs.microsoft.com/en-us/cli/azure/install-azure-cli) for local testing.
3. **GitHub Secrets**: Set up the following secrets in your GitHub repository:
   - `AZUREAPPSERVICE_CLIENTID`: The client ID for Azure App Service.
   - `AZUREAPPSERVICE_TENANTID`: Your Azure Tenant ID.
   - `AZUREAPPSERVICE_SUBSCRIPTIONID`: Your Azure Subscription ID.

### Usage

1. Clone this repository and navigate into it:
    ```bash
    git clone https://github.com/yourusername/azure-functions-deployment-template.git
    cd azure-functions-deployment-template
    ```

2. Add your function code and update `requirements.txt` with the necessary packages.

3. Push your changes to the `master` branch or trigger the workflow manually through GitHub Actions.

4. The GitHub Actions workflow will handle the following:
   - Python setup and dependencies installation.
   - Azure login using provided secrets.
   - Deployment of your Function App to Azure.

## Workflow File Details

Below is a brief explanation of each step in the workflow file:

- **Checkout repository**: Fetches your repository’s latest code.
- **Setup Python**: Configures Python version 3.11 for the deployment environment.
- **Install dependencies**: Installs any Python packages listed in `requirements.txt`.
- **Login to Azure**: Authenticates with Azure using the client ID, tenant ID, and subscription ID provided in GitHub secrets.
- **Deploy to Azure Functions**: Deploys the application package to Azure, utilizing `.funcignore` and additional deployment flags.
- **Remove obsolete settings**: Deletes certain app settings that may conflict with the deployment.
- **Set FUNCTIONS_WORKER_RUNTIME**: Ensures that `FUNCTIONS_WORKER_RUNTIME` is set to Python for correct runtime handling.

## Customization

- Update the `env` variables at the beginning of `deploy.yml` to customize the function app name, resource group, and Python version.

---

## Additional Resources

- [GitHub Actions Documentation](https://docs.github.com/en/actions)
- [Azure Functions Documentation](https://docs.microsoft.com/en-us/azure/azure-functions/)
- [Azure CLI Documentation](https://docs.microsoft.com/en-us/cli/azure/)

---

## License

This repository is licensed under the MIT License. See `LICENSE` for more information.
