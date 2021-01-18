# quarkus-graphql project

This codebase came from [Microservices with Quarkus by Duminda Wanninayake](https://dumisblog.wordpress.com/2020/03/03/microservices-with-quarkus-graphql-api-reactive-mysql/)

This project uses Quarkus, the Supersonic Subatomic Java Framework.

## Running the application in dev mode

You can run your application in dev mode that enables live coding using:
```
./mvnw quarkus:dev
```

# GraphQL API

Open up localhost:8080/graphql-ui/ and query with:

```graphql
{
  bookById(id:"book-1"){
    id
    name
    pageCount
    author {
      firstName
      lastName
    }
  }
}
```

Then we get back:

```json
{
  "data": {
    "book1": {
      "id": "book-1",
      "name": "Harry Potter and the Philosopher's Stone",
      "pageCount": 223,
      "author": {
        "firstName": "Joanne",
        "lastName": "Rowling"
      }
    }
  }
}
```

## Creating a native executable

```shell
# Before building the docker image run:
mvn package -Pnative -Dquarkus.native.container-build=true

# Then, build the image with:
docker build -f src/main/docker/Dockerfile.native -t quarkus/microprofile-graphql-quickstart .

# Then run the container using:
docker run -i --rm -p 8080:8080 quarkus/microprofile-graphql-quickstart
```
