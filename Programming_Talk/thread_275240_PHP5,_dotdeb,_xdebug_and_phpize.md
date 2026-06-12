---
title: "PHP5, dotdeb, xdebug and phpize"
date: 2006-10-11
forum: Programming Talk
---

### Post by moreweb on 2006-10-11
Hi all,
I've a problem to install xdebug on php5 using dotdeb repository.
Is it possible? On dotdeb repository there isn't **php5-xdebug** (like php4 version).

So I've tried with pecl but I've got a *generic phpize error*:
```
marco@moreweb:~$ sudo pecl install xdebug-beta
Password:
downloading xdebug-2.0.0RC1.tgz ...
Starting to download xdebug-2.0.0RC1.tgz (252,286 bytes)
.....................................................done: 252,286 bytes
64 source files, building
running: phpize
Configuring for:
PHP Api Version:         20041225
Zend Module Api No:      20050922
Zend Extension Api No:   220051025
ERROR: `phpize' failed

```
Someone suggest me to use ubuntu repository with PHP 5.1.2. Ok, but I've used dotdeb because some times ago on standard repositories there aren't some php features like PDO (php5-* package).

Some info:
```
marco@moreweb:~$ dpkg -l | grep -i php5
ii  libapache-mod-php5                5.1.6-0.dotdeb.2                       PHP 5 scripting language - apache 1.3 module
ii  libapache2-mod-php5               5.1.6-0.dotdeb.2                       PHP 5 scripting language - apache 2.0 module
ii  php5                              5.1.6-0.dotdeb.2                       server-side, HTML-embedded scripting languag
ii  php5-cli                          5.1.6-0.dotdeb.2                       PHP 5 scripting language
ii  php5-common                       5.1.6-0.dotdeb.2                       Common files for packages built from the php
ii  php5-dev                          5.1.6-0.dotdeb.2                       Files for PHP5 module development
ii  php5-gd                           5.1.6-0.dotdeb.2                       GD module for php5
ii  php5-ming                         5.1.6-0.dotdeb.2                       Ming module for php5
ii  php5-mysql                        5.1.6-0.dotdeb.2                       MySQL module for php5
ii  php5-mysqli                       5.1.6-0.dotdeb.2                       MySQLi module for php5
ii  php5-pdo-mysql                    5.1.6-0.dotdeb.2                       PDO-MySQL module for php5
ii  php5-pdo-sqlite                   5.1.6-0.dotdeb.2                       PDO-SQLite module for php5
ii  php5-pear                         5.1.6-0.dotdeb.2                       PEAR - PHP Extension and Application Reposit
```

[I]I've talk about this problem in [this]("http://www.ubuntuforums.org/showthread.php?t=264223") thread also.
[/I]

Plese, someone can help me? :-|
Thanks.

---

### Post by Travis S on 2007-01-05
I just ran into this issue myself.  The problem is that php5 from dotdeb does not overwrite Ubuntu's php-config.  I used the following to compile xdebug this morning:

```

$ phpize5
$ ./configure --enable-xdebug --with-php-config=/usr/bin/php-config5
$ make

```

That forces the use of php-config5.  Of course, you could manually remove /usr/local/bin/php-config which would address the issue as well.  It is overriding the correct /usr/bin/php-config.  To make sure you're removing the correct one, run:

```

$ /usr/local/bin/php-config --version
5.1.6
$ /usr/bin/php-config --version
5.2.0-0.dotdeb.3

```

Remove whichever one displays 5.1.6 as the version.

---

