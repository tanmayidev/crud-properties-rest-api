# PostgreSQL command prompt

### `psql` is the PostgreSQL interactive terminal. Running `psql` will connect user to a PostgreSQL host.

##Connecting to default `postgres` database with default login information
`psql postgres`

### List of common commands 
* `\q` Exist `psql` connection
* `\c` Connect to a new database
* `\dt` List all tables
* `\du` List all roles
* `\list` List databases
* `\conninfo` Gives connection information like database, user and port

# Creating a role in Postgres

### Create a role `user` with password `password`. A role can function as a user or group.
`postgres=# CREATE ROLE user WITH LOGIN PASSWORD 'password';`

### Allow `user` to create a database
`postgres=# ALTER ROLE user CREATEDB`

### Run `\du` to list all the roles/users
|`user` | `Create DB`| `{}` |
|-----|-----|------|
|`postgres` | `Superuser, Create role, Create DB` | `{}` |

### Exit from the default session
`postgres=# \q`

### Connect to `postgres` with `user`
`psql -d postgres -U user`

* Prompt shows `postgres=>` instead of `postgres=#`, meaning  we are no longer logged in as a superuser.

# Creating a database in Postgres

### Creating a database `api`
`postgres=> CREATE DATABASE api;`

### Connecting to `api` database with `user` using `\c` (connect) command.
`postgres=> \c api`   
`You are now connected to database "api" as user "user"`   
`api=>`

# Creating a table in Postgres

`api=> `     
`CREATE TABLE users (`      
`  ID SERIAL PRIMARY KEY,`      
`  name VARCHAR(30),`    
`  email VARCHAR(30)`    
`);`   

* Adding entries to `users` table 
`INSERT INTO users (name, email)
  VALUES ('Jerry', 'jerry@example.com'), ('George', 'george@example.com');`
  
* To see the entries in `users`  
`api=> SELECT * FROM users;`    

|id |  name  |   email  |  
|----|--------|--------------------|
|  1 | Jerry  | jerry@example.com |
|  2 | George | george@example.com|


