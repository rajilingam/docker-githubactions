# docker-githubactions
What is GitHub Actions?
GitHub Actions is a continuous integration and continuous delivery (CI/CD) platform that allows developers to automate various tasks related to their software development workflows directly within the GitHub environment. With GitHub Actions, developers can define custom workflows using YAML syntax to specify the steps and conditions for executing tasks such as building, testing, deploying, and releasing software.

What are Workflows?
Workflows are a set of automated steps that are triggered based on certain events in your GitHub repository. These events can include pushing code to the repository, creating pull requests, or releasing a new version. Workflows are defined using YAML syntax and are stored in a .github/workflows directory in your repository.

Run the Workflow locally:
While GitHub Actions is great for automating your workflow, running your actions locally on your machine can be helpful. Running actions locally allows you to test your workflows in a more controlled environment and ensure they’re working as expected before pushing changes to your repository. GitHub Actions is a powerful tool that allows you to automate your software development workflows in a very efficient way.
link:
https://medium.com/overcast-blog/build-push-the-docker-image-to-docker-hub-using-github-actions-74f20d47c483
Step 1: Create a dockerfile
To build the docker image we need to create a dockerfile.
For this tutorial, I will create a very basic dockerfile and build the image using that.
Create Dockerfile & add the below code to it.


The above code will build the image on top of the Apache image using our custom index.html which we will create in the next step.
Step 2: Create index.html file
Create index.html file & add the below code to it.

Step 3: Store the docker hub credentials
To push the docker image to docker hub we first need to log into docker hub so, for that we need to store the docker hub’s credentials in the secrets.
In your repository, store the credentials in the secrets.

Step 4: Create the GitHub actions workflow
Now create the .github/workflow/image-build.yml file and add the below code to it.

The above workflow will trigger on every commit in the main branch.
The workflow will use the secrets (username & password) and log in to the docker hub.
Step 5: Commit the code
Now, commit the code to your GitHub repository & as soon as you commit you will see the workflow is running.
tep 6: Verify the changes
Once the workflow runs successfully you can see the image will be there in your docker hub.

Summary
Workflow Name: Describes the workflow's purpose (building a Docker image).
Trigger: The workflow runs when code is pushed to the main branch.
Job: Includes steps to:
Check out the code from your repository.
Set up Docker Buildx.
Log in to Docker Hub using secure credentials.
Build the Docker image using the specified tag.
Push the Docker image to Docker Hub.
Each step in this workflow is a command or action that helps automate the process of building and deploying a Docker image, making it easier to manage and deploy your applications.
