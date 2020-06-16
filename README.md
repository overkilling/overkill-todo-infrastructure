# overkill-todo-infrastructure

> The pleasure is to play, makes no difference what you say - Motörhead

![CI](https://github.com/overkilling/overkill-todo-infrastructure/workflows/CI/badge.svg?branch=master)

An overkill collection of infrastructure code for the Todo app

## Overview

The current architecture of the Todo application follows the Box-Box-Container model, or BBC for short.
It splits the architecture concerns into three layers: presentation, business logic and persistence.
In the context of the Todo application:

* The presentation layer is a [React Single Page Application (SPA)](https://github.com/overkilling/overkill-todo-spa-frontend)
* The business logic is a [Golang API](https://github.com/overkilling/overkill-todo-monolith-api)
* The persistence is a [Postgres database](https://www.postgresql.org/).

Below is colorful architecture diagram:

![Diagram](/.github/diagram.png?raw=true)

This is a fairly [standard architecture style](https://martinfowler.com/bliki/PresentationDomainDataLayering.html), and it could considered a good starting point for most applications.
If/when an application grows in complexity and features, other patterns could be considered, such as  microservices, event sourcing, CQRS and many more.
Hopefully these other patterns will be explored in other overkill implementations, so they can be evaluated and compared.

In this simple architecture, the SPA and API components where implemented in a slighlty overkill fashion.
This means that, even though the problem space can be considered quite simple, the solution has been overengineered to exercise and highlight certain techniques and methodologies.
E.g. both `BasicAuth` and `JWT` authentication methods will be supported, it will include REST and `GraphQL` APIs, logs and metrics will be gathered.
The intent is to provide some practice to the developer and, perhaps, some education to the readers.

This repository contains infrastructure related code, which ties the whole application together.
It allows to start the application locally through `docker-compose`, but it doesn't deploy it yet to any real environment.

## Getting started

To get started, clone the codebase to your local environment:

```
git clone git@github.com:overkilling/overkill-todo-infrastructure.git
```

### Running the application

Currently the only supported mechanism for running the application is through `docker-compose`.

To run the full stack (frontend, backend and database) with the latest versions (from `docker/versions.json`):

```
bin/docker-compose-with-versions -f docker/docker-compose.spa_api_monolith.yml up --build
```

### Pact

Currently the shared contract between frontend and backend is stored in `pacts/spa-api.json`.
At some point this will be moved to a Pact broker.

### Github Actions

TODO

