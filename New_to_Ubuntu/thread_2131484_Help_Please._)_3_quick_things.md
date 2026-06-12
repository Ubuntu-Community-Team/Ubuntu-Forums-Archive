---
title: "Help Please. :) 3 quick things"
date: 2013-04-01
forum: New to Ubuntu
---

### Post by bt1996 on 2013-04-01
Hello,

I very new to this and I was wondering what commands do I need to run to download these 3 programs:

[LIST]
[*]Java runtime
[*]Webserver with PHP 5.2 support
[*]SQLite or MySQL [PDO]("http://php.net/manual/en/book.pdo.php") extension for PHP 

Many Thanks
[/LIST]

---

### Post by tgalati4 on 2013-04-01
Open a terminal:

```
apt-cache search jre
sudo apt-get install default-jre
```

Install any other java components that you want.

I like *tasksel* for installing the LAMP stack.

```
sudo apt-get install tasksel
sudo tasksel
```

I'm not familiar with how the PDO extensions get loaded:

tgalati4@Mint14-Extensa ~/Desktop $ apt-cache search php pdo
php5-mysql - MySQL module for php5
php5-odbc - ODBC module for php5
php5-pgsql - PostgreSQL module for php5
php5-sqlite - SQLite module for php5
doctrine - Tool for object-relational mapping in PHP
php-db - PHP PEAR Database Abstraction Layer
php-mdb2 - merge of the PEAR DB and Metabase php database abstraction layers
php5-mysqlnd - MySQL module for php5 (Native Driver)
php5-sybase - Sybase / MS SQL Server module for php5

It's possible that it is contained in one of the above.  If that is the case then for mysql:

```
sudo apt-get install php5-mysql
```

Try to keep your posts limited to one question per post.  It makes it easier to respond to.

---

