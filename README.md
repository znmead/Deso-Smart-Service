# Deso Smart Services
This project serves as a simple implementation example (framework) of [Deso](https://deso.org) Protocol's [Smart Services](https://www.deso.org/blog/smart-services). This framework comes with out-of-the-box SSL, MongoDB, dev/stage/prod enviornments, and modularity.

# Structure
The structure of this repo is as follows:

- Config - Stores all project configuration for Docker, Nginx, Git, MongoDB, and etc
    - data - Any requiered project data, such as local Mongo data for development or certbot data for production
- Scripts - Includes helpful utils for running the project in dev, stage, and prod. See [Development & Deployment](#development-and-deployment) for more details.
- Src
    - Db - Stores database-related interactions
    - Events - Event listeners, including trigger()
    - Global - Global data such as constant values
    - Router - The router which handles incoming REST requests
    - Types - Custom types used throughout the project
    - Utils - Utility functions for repeate code & source modularity

# Development & Deployment
To deploy the application in Development, you can utilize the `app.sh` script. It takes a few possible arguments:
    - Action
        - up - Starts the application
        - build - Builds a new App image (This is needed when files are added)
        - restart - Restarts the App service inside of Compose
    - Enviornment
        - dev
        - stage
        - prod

When building for production, you will also want to utilize the `init-letsencrypt.sh` script if you plan on using SSL. This will initalize Certbot and create a dummy SSL cert to then validate the creation of a free Let's Encrypt Certificate. This script only has to be ran once (The first time setting up the project), and requiers an existing A record pointed at the server's IP.