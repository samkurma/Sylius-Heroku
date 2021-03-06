Sylius Heroku Edition
=====================

This is a Heroku enabled fork of Sylius. Please see the [blog post][]
for more details.

[blog post]: http://christophh.net/2013/10/19/sylius-on-heroku/

Install
-------

```sh
$ git clone git://github.com/CHH/Sylius-Heroku
$ cd Sylius-Heroku
$ heroku create --region eu --buildpack git://github.com/CHH/heroku-buildpack-php
$ heroku labs:enable user-env-compile
$ heroku addons:add mandrill:starter
$ heroku addons:add heroku-postgresql:dev
# Replace COLOR with the color in the output of the previous command
# so it looks like e.g. HEROKU_POSTGRESQL_GRAY_URL
$ heroku pg:promote HEROKU_POSTGRESQL_COLOR_URL
$ git push heroku master
$ heroku run php app/console sylius:install --env=prod
# Rebuild Assetic assets
$ git commit -m "Rebuild assets" --allow-empty && git push heroku master
# View your shop in your browser!
$ heroku open
```

Update
------

You need [Composer](http://getcomposer.org) to update.

```sh
$ git pull git://github.com/Sylius/Sylius master
$ composer update
$ git commit -am "Update dependencies"
$ git push heroku master
```

Sylius [![Build status...](https://secure.travis-ci.org/Sylius/Sylius.png?branch=master)](http://travis-ci.org/Sylius/Sylius) [![Scrutinizer Quality Score](https://scrutinizer-ci.com/g/Sylius/Sylius/badges/quality-score.png?s=f6d89b8aad6e15cab61134e7c0544ee1313f7f31)](https://scrutinizer-ci.com/g/Sylius/Sylius/)
======

Sylius is an open source e-commerce solution for **PHP**, based on the [**Symfony2**](http://symfony.com) framework.

Ultimate goal of the project is to create a webshop engine, which is user-friendly, *loved* by developers and has a helpful community.

Sylius is constructed from fully decoupled components (bundles in Symfony2 glossary), which means that every feature (products catalog, shipping engine, promotions system...) can be used in any other application. 

We're using full-stack BDD methodology, with [phpspec](http://phpspec.net) and [Behat](http://behat.org).

Documentation
-------------

Documentation is available at [docs.sylius.org](http://docs.sylius.org).

Quick Installation
------------------

``` bash
$ wget http://getcomposer.org/composer.phar
$ php composer.phar create-project sylius/sylius -s dev
$ cd sylius
$ php app/console sylius:install
```

[Behat](http://behat.org) scenarios
-----------------------------------

You need to copy Behat default configuration file and enter your specific ``base_url``
option there.

```bash
$ cp behat.yml.dist behat.yml
$ vi behat.yml
```

Then download [Selenium Server](http://seleniumhq.org/download/), and run it.

```bash
$ java -jar selenium-server-standalone-2.11.0.jar
```

You can run Behat using the following command.

``` bash
$ bin/behat
```

Troubleshooting
---------------

If something goes wrong, errors & exceptions are logged at the application level.

````
tail -f app/logs/prod.log
tail -f app/logs/dev.log
````

Contributing
------------

All informations about contributing to Sylius can be found on [this page](http://docs.sylius.org/en/latest/contributing/index.html).

Sylius on twitter
-----------------

If you want to keep up with the updates, [follow the official Sylius account on twitter](http://twitter.com/Sylius).

Bug tracking
------------

Sylius uses [GitHub issues](https://github.com/Sylius/Sylius/issues).
If you have found bug, please create an issue.

MIT License
-----------

License can be found [here](https://github.com/Sylius/Sylius/blob/master/LICENSE).

Authors
-------

Sylius was originally created by [Paweł Jędrzejewski](http://pjedrzejewski.com).
See the list of [contributors](https://github.com/Sylius/Sylius/contributors).
