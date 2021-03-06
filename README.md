[![Tests](https://github.com/poseidonphp/laravel-env-sync/actions/workflows/php.yml/badge.svg?branch=main)](https://github.com/poseidonphp/laravel-env-sync/actions/workflows/php.yml)
[![Scrutinizer](https://img.shields.io/scrutinizer/g/poseidonphp/laravel-env-sync.svg?maxAge=1800)](https://scrutinizer-ci.com/g/poseidonphp/laravel-env-sync/?branch=main)
[![Scrutinizer Code Quality](https://scrutinizer-ci.com/g/poseidonphp/laravel-env-sync/badges/quality-score.png?b=main)](https://scrutinizer-ci.com/g/poseidonphp/laravel-env-sync/?branch=main)
[![Build Status](https://scrutinizer-ci.com/g/poseidonphp/laravel-env-sync/badges/build.png?b=main)](https://scrutinizer-ci.com/g/poseidonphp/laravel-env-sync/build-status/main)
[![Code Coverage](https://scrutinizer-ci.com/g/poseidonphp/laravel-env-sync/badges/coverage.png?b=main)](https://scrutinizer-ci.com/g/poseidonphp/laravel-env-sync/?branch=main)
[![Code Intelligence Status](https://scrutinizer-ci.com/g/poseidonphp/laravel-env-sync/badges/code-intelligence.svg?b=main)](https://scrutinizer-ci.com/code-intelligence)

# Laravel Env Sync

Keep your .env in sync with your .env.example or vice versa.

It reads the .env.example file and makes suggestions to fill your .env accordingly. 

This package is an updated version of the one formerly maintained by jtant/laravel-env-sync which has been abandoned. It is designed to work with Laravel v8+.

## Installation via Composer

Start by requiring the package with composer

```
composer require poseidonphp/laravel-env-sync
```

## Usage

### Sync your envs files

You can populate your .env file from the .env.example by using the `php artisan env:sync` command.

The command will tell you if there's anything not in sync between your files and will propose values to add into the .env file.

You can launch the command with the option `--reverse` to fill the .env.example file from the .env file

You can also use `--src` and `--dest` to specify which file you want to use. You must use either both flags, or none.

If you use the `--no-interaction` flag, the command will copy all new keys with their default values.

### Check for diff in your envs files

You can check if your .env is missing some variables from your .env.example by using the `php artisan env:check` command.

The command simply show you which keys are not present in your .env file. This command will return 0 if your files are in sync, and 1 if they are not, so you can use this in a script

Again, you can launch the command with the option `--reverse` or with `--src` and `--dest`.

The command will also dispatch event `Poseidonphp\LaravelEnvSync\Events\MissingEnvVars`, which will contain the missing env variables, which could be used in automatic deployments. Event is only fired when there are missing env variables.

### Show diff between your envs files

You can show a table that compares the content of your env files by using the `php artisan env:diff` command.

The command will print a table that compares the content of both .env and .env.example files, and will highlight the missing keys.

You can launch the command with the options `--src` and `--dest`.
