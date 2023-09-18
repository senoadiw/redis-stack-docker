# redis-stack-docker
Run Redis Stack on Docker.

Based on the following image:
* https://hub.docker.com/r/redis/redis-stack

## Requirements
* Docker and Docker Compose installed
  * https://docs.docker.com/engine/install/
* for Linux: the user must belong the docker group to allow running `docker` without `sudo` privilege
  * `sudo usermod -aG docker ${USER}`

## How to run
SSH to the target server and run:
```
git clone https://github.com/senoadiw/redis-stack-docker.git

cd redis-stack-docker

# define environment variables (optional)
cp .env.sample .env
nano .env

# bring up the container
docker compose up -d

# check the logs and wait a moment for the container to initialize
docker compose logs -f

# done!

# access redis-cli on the container
docker compose exec -it redis redis-cli

# to stop the container
docker compose stop

# to start the container
docker compose up -d

# to delete the container
docker compose down

# to delete the container and volume (warning: this will delete ALL persistent data)
docker compose down -v
```

## Daemon and Management
The Redis daemon will listen on the default port of 6379.

RedisInsight is available by accessing `http://localhost:8001`.
