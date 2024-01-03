
## Description
In this project, I learned how to develop several small, self-contained, loosely coupled microservices  
that will communicate with one another and a simple front-end application with a REST API, with RPC, over  
gRPC, and by sending and consuming messages using AMQP, the Advanced Message Queuing Protocol. The built  
microservices include the following functionality:

* A Front End service, that displays web pages;

* An Authentication service, with a Postgres database;

* A Logging service, with a MongoDB database;

* A Listener service, which receives messages from RabbitMQ and acts upon them;

* A Broker service, which is an optional single point of entry into the microservice cluster;

* A Mail service, which takes a JSON payload, converts it into a formatted email and sends it out.

Also, I learned how to deploy distributed applications to a Docker Swarm and Kubernetes, scale up and down, as necessary, and update individual microservices with little or no downtime.



## Running the project

From the project directory, execute this command (this assumes that you have 
[GNU make](https://www.gnu.org/software/make/) and a recent version
of [Docker](https://www.docker.com/products/docker-desktop) installed on your machine):

~~~
make up_build 
~~~

If the code has not changed, subsequent runs can be `makeup`.

Then start the front end:

~~~
make start
~~~

Hit the front end with your web browser at `http://localhost:4000`.

To stop everything:

~~~
make stop
make down
~~~

While working on code, you can rebuild just the service you are working on by
executing

`make auth`

Where `auth` is one of the services:

- auth
- broker
- logger
- listener
- mail

All make commands:

~~~
Choose a command:
  up                  starts all containers in the background without forcing build
  build_dockerfiles   builds all dockerfile images
  push_dockerfiles    pushes tagged versions to the docker hub
  up_build            stops docker-compose (if running), builds all projects, and starts docker-compose
  down                stop docker-compose
  build_front_linux   builds the front-end binary as a Linux executable
  build_broker        builds the broker binary as a Linux executable
  build_mailer        builds the mailer binary as a Linux executable
  build_logger        builds the logger binary as a Linux executable
  build_listener      builds the listener binary as a Linux executable
  build_auth          builds the auth binary as a Linux executable
  build_front         builds the front-end binary
  start               starts the front end
  stop                stop the front end
  swarm_down          stops the swarm
  test                runs all tests
  clean               runs go clean and delete binaries
  help                displays help
~~~
