# Github Workflow configuration for Spring Cloud Stream with Asyncapi 
This repo will have the github workflow needed to plan, provision, and promote a Spring Cloud Stream application using Event Portal, Event Broker, and AsyncaPI 

- [Make your existing CICD even better](#make-your-existing-cicd-even-better)
  - [Things to note](#things-to-note)
  - [Create new repository with Event Portal GitHub Actions](#create-new-repository-with-event-portal-github-actions)
  - [Configure GitHub Actions](#configure-github-actions)
  - [Upload micro-integration to GitHub](#upload-micro-integration-to-github)
  - [Commit the files and open a pull request](#commit-the-files-and-open-a-pull-request)

## Things to note
- This workflow assumes an asyncapi.yml file in the root of the directory.
- Make sure github actions is enabled in your repo
  - Settings --> Actions --> General --> Allow all actions and reusable workflows
  - Settings --> Actions --> General --> Workflow permissions --> Enable read/write
- Confiure the secrets in your repo as per the [workflow files](.github/workflows)
- Edit this readme to match your project description

## Make your existing CI/CD even better

> [!TIP]  
> You need to have a GitHub account for this portion. If you don’t have one, you can [get one free](https://github.com/signup). 

### Create new repository with Event Portal GitHub Actions
1. Make sure you are logged into GitHub and go to the [Import Existing Repository page](https://github.com/new/import). 
2. Use `https://github.com/SolaceLabs/ep-scs-workflow` for the URL, list yourself as the owner, and name the new repository `customer360`. Click on **Begin Import**.<br>![Image](img/51.png)<br><br>
3. Wait for the import to complete, usually around 3 minutes. Then click on the link to open the repository.

> [!CAUTION]  
> Cloning through GitHub occasionally takes a bit of time. After 3 minutes, try refreshing the page to see if it's done.

### Configure GitHub Actions
1. In the top menu of the repository, select **Settings**.<br>![Image](img/52.png)<br><br>
2. In the left-hand column, select **Actions (1)**, then **General (2)**.<br>![Image](img/53.png)<br><br>
3. Scroll to the bottom of the page, and click on the radio button next to **Read and write permissions (1)**. Then click on **Save (2)**.<br>![Image](img/54.png)<br><br>
4. Again in the left-hand column, scroll down, expand **Secrets and variables (1)**, then click on **Actions (2)**.<br>![Image](img/55.png)<br><br>
5. In the main panel, click on **New Repository Secret**.<br>![Image](img/56.png)<br><br>
6. Name the secret `SOLACE_CLOUD_TOKEN`. The value of the secret should be the token you created for Postman when initially populating your account.<br>![Image](img/57.png)<br><br>

### Upload micro-integration to GitHub
1. Unzip the **Spring Cloud Stream** source code you downloaded from [studio.asyncapi.com](https://studio.asyncapi.com) on your hard drive.
2. In the root directory, move the `asyncapi.yml` file to the **template** directory. <br>![Image](img/58.png)<br><br>
3. Navigate to the **template** directory. It should look like this: <br>![Image](img/59.png)<br><br>
4. In your browser, go to the new repository, click on the **plus sign (1)**, then on **Upload files (2)**.<br>![Image](img/60.png)<br><br>
5. Select all four files/subdirectories in the **template** directory, then click on **OK**.

> [!CAUTION]  
> Do *not* upload the **template** directory. You need to upload the four files/subdirectories.

### Commit the files and open a pull request
1. In the resulting window, change the radio button to **Create a new branch for this commit**. Then click on **Propose changes**.<br>![Image](img/61.png)<br><br>
2. In the next screen, click on **Create pull request**.<br>![Image](img/62.png)<br><br>
3. The **GitHub Actions** kick off. When they are finished, there should be a list of changes that will occur should the pull request be approved.<br>![Image](img/63.png)<br><br>
4. Scroll down to the bottom of the pull request and click on **Merge pull request**. Then click on **Confirm merge**.<br>![Image](img/64.png)<br><br>
5. Using the **management console** of your cloud broker, confirm that the CICD process created the same **queues, subscriptions, ACLs** as manual promotion.
