---
title: "PGSQL and PHP"
date: 2007-12-24
forum: Programming Talk
---

### Post by kumarldh on 2007-12-24
it's been long 2 days and till date I see the following.

Warning: pg_connect() [function.pg-connect]: Cannot create new link. Too many open links (0) in /var/www/connect2PGSQL.php on line 3

Warning: pg_last_error() [function.pg-last-error]: No PostgreSQL link opened yet in /var/www/connect2PGSQL.php on line 4
Could not connect: 


Here is the server signature that tells what all is installed.
Apache/2.2.4 (Ubuntu) 
PHP/5.2.3-1ubuntu6.2 
mod_ssl/2.2.4 
OpenSSL/0.9.8e 
mod_perl/2.0.2 
Perl/v5.8.8 Server 
PostGreSQl8.1

Here is the out put of phpinfo that may be of interest

Configuration File (php.ini) Path 	/etc/php5/apache2
Loaded Configuration File 	/etc/php5/apache2/php.ini
Scan this dir for additional .ini files 	/etc/php5/apache2/conf.d
additional .ini files parsed 	/etc/php5/apache2/conf.d/gd.ini, /etc/php5/apache2/conf.d/mysql.ini, /etc/php5/apache2/conf.d/mysqli.ini, /etc/php5/apache2/conf.d/pdo_mysql.ini, /etc/php5/apache2/conf.d/pdo_pgsql.ini, /etc/php5/apache2/conf.d/pgsql.ini, 
/etc/php5/apache2/conf.d/xsl.ini


I can connect to PGSQL using PGAdmin, I created a user and even a database. I can login to command based client. But PHP seems to be hurdle. I googled around on the web and dint see anything that could help me. I have all the .ini files and .so files/extensions in place.
Any guidance will be much appreciated.

Thanks.

---

### Post by jhofmann on 2007-12-24
I would have a hard look at:

/var/www/connect2PGSQL.php on line 3

Jim

---

### Post by kumarldh on 2007-12-25
Here is the code.
[PHP]<?php
// Connecting, selecting database
$dbconn = pg_connect("host=127.0.0.1 dbname=focus user=postgres password=lamp")
    or die('Could not connect: ' . pg_last_error());
// Closing connection
pg_close($dbconn);
?>[/PHP]

My machine is a standalone machine. The password for postgres user is "lamp"

---

### Post by kumarldh on 2007-12-25
Damn it, this cant be true. I just placed these lines in php.ini and removed them from the respective ini files and things are wow now

extension=pgsql.so
extension=pdo_pgsql.so

I hate myself for this stupid mistake

---

### Post by sbnimbalkar on 2009-05-02
> **kumarldh said:**
> Damn it, this cant be true. I just placed these lines in php.ini and removed them from the respective ini files and things are wow now

extension=pgsql.so
extension=pdo_pgsql.so

I hate myself for this stupid mistake

Thanks Kumarldh for solving the problem which I was grappling for past three days. Tried reloading each package again and again, googled around (just to see the message that it was a bug in Php4, not Php5). 

Thanks again :P

---

### Post by rockcesar on 2011-06-23
Thank so much, that is what I was looking for. I moved from

/etc/php5/apache2/conf.d/pgsql.ini
/etc/php5/apache2/conf.d/pdo_pgsql.ini

To:

/etc/php5/apache2/php.ini

In the Postgresql section.

---

### Post by slavik on 2011-06-23
and stay dead.

---

