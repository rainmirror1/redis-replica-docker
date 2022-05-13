# Build

## Primary node

`docker build ./primary/ -t redis-primary`

## Replica node

`docker build ./replica/ -t redis-replica`

# Run

`docker run --name redis-prim-1 -d -p 16379:6379 redis-primary && docker run --name redis-repl-1 -d -p 26379:6379 --add-host host.docker.internal:host-gateway redis-replica` [^1]

# Connect

## Primary node

`docker run --rm -it --add-host host.docker.internal:host-gateway redis redis-cli -h host.docker.internal -p 16379` [^1]

## Replica node

`docker run --rm -it --add-host host.docker.internal:host-gateway redis redis-cli -h host.docker.internal -p 26379` [^1]

[^1]: For Mac, don't need to use parameter `--add-host host.docker.internal:host-gateway`
