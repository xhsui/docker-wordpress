# docker-wordpress
#### 1. 拷贝一份docker-compose的示例作为你的docker-compose配置文件
```shell
copy docker-compose.yaml.example docker-compose.yaml
```

#### 2. 编辑你需要的参数
```shell
version: "3"
services:
   db:
     image: mysql:5.7
     volumes:
       - ./db_data/:/var/lib/mysql/:rw
     restart: always
     environment:
       MYSQL_ROOT_PASSWORD: somewordpress
       MYSQL_DATABASE: wordpress
       MYSQL_USER: wordpress
       MYSQL_PASSWORD: wordpress

   wordpress:
     depends_on:
       - db
     image: wordpress:latest
     volumes:
      - ./code_data/:/var/www/html/:rw
     ports:
       - "8000:80"
     restart: always
     environment:
       WORDPRESS_DB_HOST: db:3306
       WORDPRESS_DB_USER: wordpress
       WORDPRESS_DB_PASSWORD: wordpress

```
