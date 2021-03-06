## Laravel API Boilerplate (JWT Edition) + React Slingshot

Laravel API Boilerplate is a "starter kit" you can use to build your first API in seconds. As you can easily imagine, it is built on top of the awesome Laravel Framework. This version is built on Laravel 5.3!

It is built on top of three big guys:

* JWT-Auth - [tymondesigns/jwt-auth](https://github.com/tymondesigns/jwt-auth)
* Dingo API - [dingo/api](https://github.com/dingo/api)
* Laravel-CORS [barryvdh/laravel-cors](http://github.com/barryvdh/laravel-cors)

What I made is an integration of these three packages and a setup of some authentication and credentials recovery methods.

## Installation

### Server installation

```sh
$ git clone https://github.com/svitekpavel/react-slingshot-laravel.git
$ cd react-slingshot-laravel
$ composer update
$ sqlite3 database/database.sqlite ""
$ php artisan migrate
$ php artisan key:generate
$ php artisan jwt:generate
```

### Client installation

```sh
$ cd client-app
$ yarn    # or `npm install`
```

That's it :-) For more information, navigate to [README](client-app/README.md) in client-app directory.

## Usage

I wrote a couple of articles on this project that explain how to write an entire sample application with this boilerplate. They cover the older version of this boilerplate, but all the concepts are the same. You can find them on Sitepoint:

Just be aware that some options in the `config/boilerplate.php` file are changed, so take a look to it.

* [How to Build an API-Only JWT-Powered Laravel App](https://www.sitepoint.com/how-to-build-an-api-only-jwt-powered-laravel-app/)
* [How to Consume Laravel API with AngularJS](https://www.sitepoint.com/how-to-consume-laravel-api-with-angularjs/)

## Start

### Start server

Start the server with `php artisan serve`. This will start your server on http://localhost:8000/.

### Start client

```
$ cd client-app
$ yarn start
```

The client application should be opened in your browser automatically. If not, navigate to http://localhost:3002/.

Webpack will watch for file changes and will run lint, tests and reload the application in browser automatically.

### Accessing API

If everything works, you should be able to see a sample message on
http://localhost:8000/api/hello

`{"message":"This is a simple example of item returned by your APIs. Everyone can see it."}`

Now you can start building your API.

## Main Features

### A Ready-To-Use Authentication Controllers

You don't have to worry about authentication and password recovery anymore. I created four controllers you can find in the `App\Api\V1\Controllers` for those operations.

For each controller there's an already setup route in `routes/api.php` file:

* `POST api/auth/login`, to do the login and get your access token;
* `POST api/auth/signup`, to create a new user into your application;
* `POST api/auth/recovery`, to recover your credentials;
* `POST api/auth/reset`, to reset your password after the recovery;

### A Separate File for Routes

All the API routes can be found in the `routes/api.php` file. This also follow the Laravel 5.3 convention.

### Secrets Generation

Every time you create a new project starting from this repository, the _php artisan jwt:generate_ command will be executed.

## Configuration

As I already said before, this boilerplate is based on _dingo/api_ and _tymondesigns/jwt-auth_ packages. So, you can find many informations about configuration <a href="https://github.com/tymondesigns/jwt-auth/wiki/Configuration" target="_blank">here</a> and <a href="https://github.com/dingo/api/wiki/Configuration">here</a>.

However, there are some extra options that I placed in a _config/boilerplate.php_ file:

* `sign_up.release_token`: set it to `true` if you want your app release the token right after the sign up process;
* `reset_password.release_token`: set it to `true` if you want your app release the token right after the password reset process;

There are also the validation rules for every action (login, sign up, recovery and reset). Feel free to customize it for your needs.

## Creating Endpoints

You can create endpoints in the same way you could to with using the single _dingo/api_ package. You can <a href="https://github.com/dingo/api/wiki/Creating-API-Endpoints" target="_blank">read its documentation</a> for details. After all, that's just a boilerplate! :)

However, I added some example routes to the `routes/api.php` file to give you immediately an idea.

## Cross Origin Resource Sharing

If you want to enable CORS for a specific route or routes group, you just have to use the _cors_ middleware on them.

Thanks to the _barryvdh/laravel-cors_ package, you can handle CORS easily. Just check <a href="https://github.com/barryvdh/laravel-cors" target="_blank">the docs at this page</a> for more info.

## Feedback

I currently made this project for personal purposes. I decided to share it here to help anyone with the same needs. If you have any feedback to improve it, feel free to make a suggestion, or open a PR!
