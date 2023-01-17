# golang-graphql
A graphql server project using golang and gqlgen (https://gqlgen.com/getting-started/).

1. For generate the graphql skeleton:

```bash
go run github.com/99designs/gqlgen init
```

2. For running application:

```bash
go run cmd/server/server.go
```

3. Create dabase using the sqlite3:

```
sqlite3 data.db
create table categories (id string, name string, description string);
```

4. After the create table, access the playground using the url: http://localhost:8080/

5. In input of web page, put the value, and after click in play button:

```graphql
mutation createCategory {
  createCategory(input: {name: "tech", description: "courses"}){
    id,
    name,
    description
  }
}

mutation createCourse {
  createCourse(input: {name: "Java", description: "learning fundamentals of java", categoryId: "352f4af6-c317-4cff-bb01-c1b68799b0aa"}) {
    id
    name
  }
}

query queryCategories {
  categories {
    id
    name
    description
  }
}

query queryCategoriesWithCourses {
  categories {
    id
    name
    courses {
      id
      name
    }
  }
}

query queryCouses {
  courses {
    id
    name
  }
}




```

6. create table of courses:

```
sqlite3 data.db
create table courses (id string, name string, description string, category_id string);
```

7. For generate the of model and types:

```
go run github.com/99designs/gqlgen generate

```