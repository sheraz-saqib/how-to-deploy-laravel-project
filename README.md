
# DEPLOY THE LARAVEL PROJECT (2025)


## Deployment

To deploy this project run all cmd one by one

```bash
php artisan optimize
```
```bash
php artisan config:clear
php artisan route:clear
php artisan view:clear
php artisan cache:clear
```
## create .htaccess file and copy this code
```.htaccess ```
then copy this code 
```bash
<IfModule mod_rewrite.c>

    RewriteEngine On

    RewriteCond %{REQUEST_FILENAME} -d [OR]
    RewriteCond %{REQUEST_FILENAME} -f
    RewriteRule ^ ^$1 [N]

    RewriteCond %{REQUEST_URI} (\.\w+$) [NC]
    RewriteRule ^(.*)$ public/$1

    RewriteCond %{REQUEST_FILENAME} !-d
    RewriteCond %{REQUEST_FILENAME} !-f
    RewriteRule ^ index.php

</IfModule>


```
create the index.php file in root directory  (recommended)
```bash

<?php

$publicPath = getcwd();

$uri = urldecode(
    parse_url($_SERVER['REQUEST_URI'], PHP_URL_PATH) ?? ''
);

// This file allows us to emulate Apache's "mod_rewrite" functionality from the
// built-in PHP web server. This provides a convenient way to test a Laravel
// application without having installed a "real" web server software here.
if ($uri !== '/' && file_exists($publicPath.$uri)) {
    return false;
}

require_once $publicPath.'/public/index.php';

```
# or 
then copy the file form this path 
```bash
C:\xampp\htdocs\{{your-project-name}}\vendor\laravel\framework\src\Illuminate\Foundation\resources\server.php
```
## config the .env file change this variable value 
```bash
APP_NAME=your-project-value 
APP_ENV=production
APP_KEY= your-project-app-key
APP_DEBUG=false
APP_URL=http://localhost
```
✌ congratulations your project now live 😁
