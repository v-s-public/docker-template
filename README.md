# Lite Docker environment for local development with Laravel
## Containers
* PHP (+ composer)
* Nginx
* MySQL
* PostgreSQL
* NPM (disposable|removable)
## Setup
1. Clone repository
2. Go to folder with cloned repository.
3. Run `docker-compose up -d --build`   
4. Place your code to `./src` folder

    4.1. With git
    * `git clone https://github.com/user/repo.git ./src`
    * `docker-compose exec app composer install`

    4.2. Create new project with composer
    * `docker-compose exec app composer create-project laravel/laravel ./`
    
5. Setup database connection in your `.env` file:


      MySQL:
      
            DB_CONNECTION=mysql
         
            DB_HOST=mysql
         
            DB_PORT=3306
         
            DB_DATABASE=laravel
         
            DB_USERNAME=laravel
         
            DB_PASSWORD=secret



      Or PostgreSQL:

            DB_CONNECTION=pgsql
         
            DB_HOST=postgres
         
            DB_PORT=5432
         
            DB_DATABASE=laravel
         
            DB_USERNAME=laravel
         
            DB_PASSWORD=secret
   
6. Run migrations: `docker-compose exec app php artisan migrate`

Now your application available by http://localhost:8080

## Available commands
### Composer
`docker-compose exec app composer [composer_command]`
### PHP and artisan
`docker-compose exec app php [options] [-f] <file> [--] [args...]`

`docker-compose exec app php artisan [artisan_command]`
### npm
Container is created to execute a npm command and will be removed after command execution.

`docker-compose run -rm npm install`

`docker-compose run -rm npm run dev`

`docker-compose run -rm npm run watch-poll`
## Volumes
Named volumes are used here. Physically located in `/var/lib/docker/volumes/`. Available to users with `sudo` rights.
* volumes list - `docker volume ls`
* inspect volume - `docker volume inspect test_mysqldbvolume`