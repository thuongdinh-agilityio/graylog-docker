# Graylog Docker POC

## Target
 - Run graylog with docker/docker-compose
 - Transfer log from another docker containers to graylog with UDP GELF

## Requirements
 - Docker version 1.12.3
 - Docker Compose version 1.8.1

## Steps

1. Up docker-compose

	```
	$ docker-compose up -d
	```

2. Add new UDP GELF Input
 - Go to http://localhost:9000 and login with admin/admin
 - Go to http://localhost:9000/system/inputs
 - Choose UDP GELF and click "Launch new input"
 - Keep all config are default

3. Simulate message from another container

	```
	$ docker run --log-driver=gelf --log-opt gelf-address=udp://localhost:12201 busybox echo Hello Graylog
	```

4. See new messages from search dashboard http://localhost:9000/search