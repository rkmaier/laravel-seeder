# Laravel Seeder

[![Build Status](https://travis-ci.org/eighty8/laravel-seeder.svg?branch=master)](https://travis-ci.org/eighty8/laravel-seeder)
[![Coverage Status](https://coveralls.io/repos/github/eighty8/laravel-seeder/badge.svg?branch=develop)](https://coveralls.io/github/eighty8/laravel-seeder?branch=master)

Have you ever wanted to seed your database in the same way you define and manage database tables in Laravel? Have you ever been confused about where you should seed data for your databases?

Have you ever wanted to seed a production database with different data from what you use in development? What if you want to 
seed a table you've added to a database that is currently in production with new data?

This project takes the database migration features in Laravel and extends them to database seeders, making them "migratable". 
All of the functionality you have grown accustomed to with Laravel migrations have been mirrored for simple database seeding!

Requirements
============

- Laravel >= 5.4 OR Lumen >= 5.6
- PHP >= 7.1

Installation
============

Install the package via Composer:

```
composer require eighty8/laravel-seeder
```

Register the service provider:

```
Eighty8\LaravelSeeder\SeederServiceProvider::class
```

Publish the configuration files:

```
php artisan vendor:publish
``` 

Enjoy!

Features
============

- Allows you to seed databases in different or all environments with different values.
- Allows you to "version" seeders the same way that Laravel handles database migrations. Running ```php artisan seed``` will only run seeds that haven't already been run.
- Allows you to rollback seeders just like database migrations 
- Allows you to run multiple seeders for the same model/table
- Allows you generate new seeders via CLI
- Prompts you if your database is in production

Usage
============
When you install LaravelSeeder, various artisan commands are made available to you which use the same methodology you're used to using with Migrations.

<table>
    <tr><td>seed</td><td>Runs all the seeds in the "seeders" directory that haven't been run yet.</td></tr>
    <tr><td>seed:rollback</td><td>Rolls back the previous batch of seeders (note that this does not affect auto-incrementing columns).</td></tr>
    <tr><td>seed:reset</td><td>Rolls back all the seeders.</td></tr>
    <tr><td>seed:refresh</td><td>Resets and re-runs all seeds.</td></tr>
    <tr><td>seed:status</td><td>Gets the status of each migratable seeder.</td></tr>
    <tr><td>seed:make</td><td>Generates a new Seeder class in the environment you specify.</td></tr>
</table>

Local Development
============
A Dockerfile with PHP 7.2, XDebug and Composer installed is bundled with the project to facilitate local development.

To easily bring up the local development environment, use the Docker Compose configuration:

```
docker-compose up -d --build
```

By default, the entrypoint script will install the Composer dependencies for you.

To run the test suite, execute the following:

```
docker-compose exec laravel-seeder test.sh
```

To run the code coverage suite, execute the following:
```
docker-compose exec laravel-seeder code-coverage.sh
```

Happy coding!