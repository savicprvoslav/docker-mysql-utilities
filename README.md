# docker-mysql-utilities

Create Docker container with mysql utilities .


## Build the image

```
docker build -t mysql/utils:1.0 .
```
## Run the container with the link to the mysql container

```
docker run -i -t --link mysql:mysql mysql/utils:1.0 bash
```

## After running the container execute next command to see the diff

```
mysqldiff --server2=root:xxx@mysql:3306 --server1=root:xxx@mysql:3306 --difftype=sql --force   --changes-for=server2 newDb:oldDb
```

## Run And Diff in the same time

Execute next oneliner to get diff , you can pipe it to a file using ``` > diff.sql ```

```
docker run -i -t --link mysql:mysql mysql/utils:1.0 sh -c "mysqldiff --server2=root:xxx@mysql:3306 --server1=root:xxx@mysql:3306 --difftype=sql --force   --changes-for=server2 newDb:oldDb"

```

// TODO Change ubuntu image 
