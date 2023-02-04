# Cassandra example running on docker

docker-compose up

## cqlsh will be the command line tool to connect
docker exec -it cas1 cqlsh

## create db
create keyspace CityInfo with replication = {'class' : 'SimpleStrategy', 'replication_factor':1};

## declare what db you will use
use CityInfo;

CREATE TABLE cities (
 id int,
 name text,
 country text,
 PRIMARY KEY(id)
);

CREATE TABLE users (
 username text,
 name text,
 age int,
 PRIMARY KEY(username)
);

INSERT INTO cities(id,name,country) VALUES (1,'Toronto','Canada');
INSERT INTO cities(id,name,country) VALUES (2,'Ottawa','Canada');
INSERT INTO cities(id,name,country) VALUES (3,'Edmonton','Canada');
INSERT INTO cities(id,name,country) VALUES (4,'Berlin','Germany');
INSERT INTO cities(id,name,country) VALUES (5,'Buffalo','USA');

INSERT INTO users(username,name,age) VALUES ('rs34','Raul Samayoa',34);
INSERT INTO users(username,name,age) VALUES ('jr23','Jack Ryan',23);
INSERT INTO users(username,name,age) VALUES ('pl34','Penny Loafer',34);

## find ip for cassandra container to connect to it
docker inspect -f '{{range.NetworkSettings.Networks}}{{.IPAddress}}{{end}}' container_name_or_id


