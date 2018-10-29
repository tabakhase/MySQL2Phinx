# MySQL2Phinx

A simple cli php script to generate a [phinx](https://github.com/robmorgan/phinx) migration from an existing MySQL database.

## Usage

```
$ php -f mysql2phinx.php [database] [user] [password] > migration.php
```

Will create an initial migration class in the file `migration.php` for all tables in the database passed. 

### custom Namespace
To generate a psr-compliant migration, supply your target namespace in `-n ""`
```
$ php -f mysql2phinx.php -- -n "My\Db\Migrations" [database] [user] [password] > migration.php
```

### custom Base Class
Use a `migration_base_class` other than `Phinx\Migration\AbstractMigration` using `-b ""`
```
$ php -f mysql2phinx.php -- -b "My\Db\AbstractMigration" [database] [user] [password] > migration.php
```

## Caveat

The `id` column will be unsigned. Phinx does not currently supported unsigned primary columns. There is [a workaround](https://github.com/robmorgan/phinx/issues/250).

MySQL `VIEW`s are **not supported** and will be silently skipped!

### TODOs

Not all phinx functionality is covered! **Check your migration code before use!**

Currently **not supported**:

* Column types:
  * [ ] `float`
  * [ ] `time`
  * [ ] `binary`
  * [ ] `boolean`
  * [ ] `double`
