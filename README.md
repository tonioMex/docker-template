## Laravel development environment based on Docker

### Features
+ Switch between PHP versions: **8.1** 、**8.2** and **8.3**.
+ Integrated with **MySQL 8**、**NGINX**、**Redis**、**adminer**、**supervisor** and **Laravel Horizon** services.
+ Customize your workspace with edit **Dockerfile** (variant by PHP Version).
+ Pre-configured **NGINX** and **supervisor** to host your laravel root directory.
+ Supported PHP extensions: **composer 2**、bcmath、exif、gd、grpc、imagick、mcrypt、pcntl、pdo_mysql、**redis**、xmlrpc、zip
+ Compare Laravel and PHP version:

|        | PHP 8.1 | PHP 8.2 | PHP 8.3 |
| ------ | -------- | ------- | ------- |
| Laravel 10 | **V** | **V** | **V** |
| Laravel 11 |       | **V** | **V** |

### Quick overview
1. Clone project
```shell
    git clone https://github.com/tonioMex/laravel-docker-template.git
```

2. Enter folder and rename **.env.example** to **.env**
```shell
    cd laravel-docker-template
    cp .env.example .env
```

3. Set **.env** file
```shell
# available version: 8.1, 8.2, 8.3
PHP_VERSION=8.3
# Your Laravel project folder
LARAVEL_APP_PATH=

# Database name
DB_NAME=
# Database user
DB_USER=
# Database passowrd and root password (use same password)
DB_PASSWORD=
```

4. Set your Laravel project **.env**
```shell
DB_CONNECTION=mysql
DB_HOST=mysql
DB_PORT=3306
DB_DATABASE=DB_NAME
DB_USERNAME=DB_USER
DB_PASSWORD=DB_PASSWORD

REDIS_HOST=redis
REDIS_PASSWORD=null
REDIS_PORT=6379
```

5. Run containers
```shell
    docker compose up -d
```

6. Install Horizon in your laravel project (otherwise your can comment **laravel-horizon** section in **docker-compose.yml** to disable it)
```shell
# enter laravel-app container
docker compose exec laravel-app /bin/bash
# install horizon packagge
compose require laravel/horizon
php artisan horizon:intall
# restart laravel-horizon container
docker compose restart laravel-horizon
```

