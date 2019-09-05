# Reliese Laravel

Reliese Laravel is a collection of Laravel Components which aim is
to help the development process of Laravel applications by
providing some convenient code-generation capabilities.

## Com instal·lar-ho a un projecte de l'IMAS

Per poder instal·lar la versió de `reliese/laravel` de l'IMAS el que hem de fer és:

1. Obrir el fitxer `composer.json`.
2. A l'array `require`, afegir la línia `"reliese/laravel": "dev-master"`

   > Exemple:
   >
   > ```json
   > "require": {
   >       ...
   >       "reliese/laravel": "dev-master",
   >       ...
   >   }
   > ```

3. Després, afegim després de l'array `require` el següent còdi:

```json
"repositories": [
        {
            "type": "git",
            "url": "git@gitlab.imasmallorca.net:llibreries-php/reliese-laravel.git"
        }
    ]
```

> NOTA: Convé que es tengui configurada la clau SSH al vostre perfil de GitLab, així no vos demanarà contrasenya per clonar el projecte.

## Models

![Generating models with artisan](https://cdn-images-1.medium.com/max/800/1*hOa2QxORE2zyO_-ZqJ40sA.png "Making artisan code my Eloquent models")

Add the `models.php` configuration file to your `config` directory and clear the config cache:

```shell
php artisan vendor:publish --tag=reliese-models
php artisan config:clear
```

### Usage

Assuming you have already configured your database, you are now all set to go.

- Let's scaffold some of your models from your default connection.

```shell
php artisan code:models
```

- You can scaffold a specific table like this:

```shell
php artisan code:models --table=users
```

- You can also specify the connection:

```shell
php artisan code:models --connection=mysql
```

- If you are using a MySQL database, you can specify which schema you want to scaffold:

```shell
php artisan code:models --schema=shop
```

### Customizing Model Scaffolding

To change the scaffolding behaviour you can make `config/models.php` configuration file
fit your database needs. [Check it out](https://github.com/reliese/laravel/blob/master/config/models.php) ;-)

### Tips

#### 1. Keeping model changes

You may want to generate your models as often as you change your database. In order
not to lose you own model changes, you should set `base_files` to `true` in your `config/models.php`.

When you enable this feature your models will inherit their base configurations from
base models. You should avoid adding code to your base models, since you
will lose all changes when they are generated again.

> Note: You will end up with two models for the same table and you may think it is a horrible idea
> to have two classes for the same thing. However, it is up to you
> to decide whether this approach gives value to your project :-)

#### Support

For the time being, this package only supports MySQL databases. Support for other databases will be added soon.
