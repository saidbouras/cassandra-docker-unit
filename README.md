## Cassandra docker 

[Apache Cassandra] is an open-source distributed storage system.

We often use an embedded single node cassandra for running integration tests , but the official image of cassandra takes around 30 seconds to start.

I try to decrease this time by tuning a little bit cassandra configuration:
- Disabling vnodes, we don't need to customize the token for testing purposes and beside we often use a single cassandra container for that.
- Disable gossip at startup, like below don't need that in a single node cassandra cluster.

With this image, the startup decrease by 2 to 3 time less than the original, depending of the cassandra version.

## Usage

Like the official image, starting a cassandra instance is simple :
```sh 
docker run --name container-name -d rinscy/cassandra:tag
```
\
In fact you can use this image in place of the official, it works exactly the same , because it was build from the cassandra official image. 
So if you want to handle connectivity (like trying to connect from an another containerized application or from  ```cqlsh```), variable environements or the volume where you used to store data... no need to change anything, all configurations are the same.
(See [cassandra] official for more advanced settings and recommendations). 

## Note
The tags are the same that exists in the official image so you can just switch easily to this image and that's it, it should work out of the box.


[cassandra]: <https://hub.docker.com/_/cassandra/>
[Apache Cassandra]: <http://cassandra.apache.org/>
