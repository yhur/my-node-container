Do you create the docker container for every nodejs or similar projects like react, loopback and so on? And even every test step during the development?

What about a container image with which you can kick off your nodejs project as the docker container by just pointing to the folder?


# my-node-container

This is the Dockerfile project to build a nodejs container which can be used mainly during development stage for the above cases.

## Usage

1. build the container image 
```docker build . -t yourContainerName```
2. create a file named `docker.run` as the entry point for the container, and place it under your node project folder.
```
#!/bin/bash
#npx serve -s build
npm run start
```
3. start the container with command line like
```
docker run -d -v /home/pi/project_folder:/home/node/app yourContainerName
``` 
or the docker-compose file such as
```
version: '3'
services:
  sample:
    container_name: sample
    image: yourContainerName
    volumes:
      - /home/pi/data/project_folder:/home/node/app

```
