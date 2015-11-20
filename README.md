# Boxel Demo
Boxel has a lot of dependencies under the hood of it. This repo will help
you get everything you need to start streaming video to minecraft.

# Setup
## Web Client
First lets get our streaming client up and running. 

```bash
cd web
npm install && bower install
gulp build
gulp serve:dist
```

A web browser should open up and look like this:

But how do we login?
We are going to need [docker-machine](https://github.com/docker/machine) to do this.

Before we build up boxel's dependencies lets build the boxel container first.
Clone [boxel]() and build the container:

```bash
docker build -t boxel .
docker images # should display boxel under REPOSITORY column
```

## Crossbar
Boxel uses [Crossbar](http://crossbar.io/) for device discovery, 
communication between the web app to the minecraft server, and to serve the web app we just saw.

## Redis
Boxel uses [Redis]() to push codec data into a pub/sub for Minecraft to use.

## PhantomJS
Boxel uses [PhantomJs]() for headless browsing to get images of websites to boxelize.

```bash
# At the root of the project
docker-machine ip <dev>
# keep track of this url and add it to the boxel service
# in the docker-compose.yml
command: "boxel -W 50 -C palettes/5bit.yml video -R docker -U ws://[docker-machine ip]/ws"
docker-compose up
```

