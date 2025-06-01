# redis
Learn Redis 
## ✅ 1. Run Redis in Docker
You can run Redis as a Docker container using the official image:
  docker run --name my-redis -p 6379:6379 -d redis --name 
  my-redis: names the container.
  -p 6379:6379: maps the container port to your host so you can access it.
  -d: runs the container in detached mode.
  redis: uses the official Redis image from Docker Hub.

### ✅ 2. Connect Using redis-cli
  There are two ways to connect using redis-cli:

🔹 Option 1: Using Another Docker Container
  docker run -it --rm --network host redis redis-cli

-network host works on Linux. 

#### For Mac/Windows, use this instead:
docker run -it --rm redis redis-cli -h host.docker.internal
-it: interactive terminal.
--rm: remove container after exit.
redis-cli -h <hostname>: connect to Redis server.
host.docker.internal: special DNS name to access host machine from Docker (for Mac/Windows).

🔹 Option 2: Exec into the Redis Container
docker exec -it my-redis redis-cli
This runs redis-cli inside the same container where Redis is running.

🔄 Example Interaction
$ docker exec -it my-redis redis-cli
127.0.0.1:6379> set foo bar
OK
127.0.0.1:6379> get foo
"bar"
🛑 Stop & Remove Redis Container
docker stop my-redis
docker rm my-redis
