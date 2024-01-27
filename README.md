###How to deploy a Go project to GCP

1. Run `go mod init example.com/hello-world` to create go.mod.
2. Create a 'main.go' file.
3. Run `go run main.go`.


## Build a docker image
1. Create a Docker file.
2. Run `docker build -t hello-world .`.


## Deploy to Google Cloud
1. Run `gcloud auth login` to login into your Google Cloud account.
2. Run `gcloud auth configure-docker [LOCATION]-docker.pkg.dev ` to configure Docker. [LOCATION] is your Google Cloud project region. For example, us-central1. If you are facing the following problem, run `gcloud auth print-access-token |sudo docker login -u oauth2accesstoken --password-stdin https://us-central1-docker.pkg.dev`.
3. Go to [Google Artifact Registry](https://cloud.google.com/artifact-registry) to create a REPOSITORY.
4. Push to docker image to registry. Run `sudo docker push [LOCATION]-docker.pkg.dev/[PROJECT]/[REPOSITORY]/hello-app`.
5. Run the service: `gcloud run deploy hello-world --image [LOCATION]-docker.pkg.dev/[PROJECT]/[REPOSITORY]/hello-app`.