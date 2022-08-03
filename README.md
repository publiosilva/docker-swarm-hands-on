# Docker Swarm Hands On

## Docker Swarm Commands

### Initialize swarm

Note: this command must be run on the manager node.

Note: Use the `--force-new-cluster` flag to use existing settings. Swarm settings are in `/var/lib/docker/swarm`.

```bash
docker swarm init --advertise-addr IP 
```

### Get command to add new worker nodes

Note: this command must be run on the manager node.

```bash
docker swarm join-token worker
```

### Get command to add new manager nodes

Note: this command must be run on the manager node.

```bash
docker swarm join-token manager
```

### Leave swarm

Note: this command must be run on the node you want to remove from the swarm.

```bash
docker swarm leave
```

### List nodes

Note: this command must be run on the manager node.

```bash
docker node ls
```

### Remove node

Note: this command must be run on the manager node.

```bash
docker node rm NODE_ID
```

### Show node details

Note: this command must be run on the manager node.

```bash
docker node inspect NODE_ID
```

### Demote a manager node

Note: this command must be run on the manager node.

```bash
docker node demote NODE_ID
```

### Restrict the execution of services on a node

Note: this command must be run on the manager node.

```bash
docker node update --availability drain NODE_ID
```

### Create service

Note: this command must be run on the manager node.

```bash
docker service create IMAGE
```

### Create service in global mode

Note: this command must be run on the manager node.

```bash
docker service create --mode global IMAGE
```

### Remove service

Note: this command must be run on the manager node.

```bash
docker service rm SERVICE_ID
```

### List services

Note: this command must be run on the manager node.

```bash
docker service ls
```

### List service tasks

Note: this command must be run on the manager node.

```bash
docker service ps SERVICE_ID
```

### Restrict service to run only on worker nodes

Note: this command must be run on the manager node.

```bash
docker service update --constraint-add node.role==worker SERVICE_ID
```

Note: To remove the above restriction, use the command `docker service update --constraint-rm node.role==worker SERVICE_ID`.

### Increase the number of replicas of a service

Note: this command must be run on the manager node.

```bash
docker service update --replicas NUMBER_OF_REPLICAS SERVICE_ID
```

Or

```bash
docker service scale SERVICE_ID=NUMBER_OF_REPLICAS
```

### Deploy stack

Note: this command must be run on the manager node.

```bash
docker stack deploy --compose-file docker-compose.yml STACK_NAME
```

### List stacks

Note: this command must be run on the manager node.

```bash
docker stack ls
```

### Remove stack

Note: this command must be run on the manager node.

```bash
docker stack rm STACK_NAME
```

## Docker Machine Commands

### Create VM

```bash
docker-machine create --virtualbox-no-vtx-check --virtualbox-cpu-count=2 -d virtualbox VM_NAME
```

### List VM

```bash
docker-machine ls
```

### Remote VM

```bash
docker-machine rm VM_NAME
```

### Start VM

```bash
docker-machine start VM_NAME
```

### Stop VM

```bash
docker-machine stop VM_NAME
```

### Access VM via SSH

```bash
docker-machine ssh VM_NAME
```
