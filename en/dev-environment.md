---
parent: For developers
title: Dev environment
nav_order: 10
---

## Setting up the dev environment with Docker Compose

### Installation
* Install [Docker](https://docs.docker.com/engine/install/) and [Docker Compose](https://docs.docker.com/compose/install/)
* Clone [the repository](https://github.com/foodcoopshop/foodcoopshop.git)
* Navigate into the root folder
* Start containers with `docker compose -f docker-compose-dev.yml up -d`
* Composer install: `docker exec -w /var/www/html fcs-web composer install`
* Npm install: `docker compose -f docker-compose-dev.yml run --rm --no-deps node bash -ci 'npm --prefix ./webroot install ./webroot'` AND `docker exec -w /var/www/html fcs-web bash ./bin/cake npm_post_install`
* Open [http://localhost:8001](http://localhost:8001) to get to the homepage
* Open [http://localhost:8080](http://localhost:8080) to get to phpmyadmin
* Be aware that the database data is lost when the docker container is shut down (tmpfs is used).


### Unit Tests
* `docker exec -w /var/www/html fcs-web php ./vendor/bin/phpunit`


### Tips for using Docker in Windows
* Install Ubuntu and switch to WSL2
* Docker Desktop: Settings / Resources / WSL Integration: Enable integration with additional distros: Enable "Ubuntu"
* Clone the repo and start docker from Ubuntu (1.000 times faster than if you start it in Windows)