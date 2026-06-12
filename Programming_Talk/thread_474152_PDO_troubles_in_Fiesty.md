---
title: "PDO troubles in Fiesty"
date: 2007-06-14
forum: Programming Talk
---

### Post by CopaceticOpus on 2007-06-14
I have a fresh install of Fiesty, which of course includes PHP 5.2.x with PDO by default. I was trying to figure out how to get pdo_dblib installed, and at one point I typed the following:

```
pecl install pdo
```

I knew I already had PDO, but I figured it wouldn't hurt. I was very wrong! PHP will not run at all on my system now. I tried "pecl uninstall pdo" and that ran, but it didn't seem to do much of anything.

When I try to restart Apache, I see the following in my /var/log/apache2/error.log:

```
PHP Warning:  PHP Startup: Unable to load dynamic library '/usr/lib/php5/20060613+lfs/mssql.so' - /usr/lib/php5/20060613+lfs/mssql.so: cannot open shared object file: No such file or directory in Unknown on line 0
/usr/sbin/apache2: symbol lookup error: /usr/lib/php5/20060613+lfs/pdo_mysql.so: undefined symbol: php_pdo_get_dbh_ce
```

How do I undo this and get PHP back to functional?

---

### Post by CopaceticOpus on 2007-06-14
I've made some progress. I forgot about the extra .ini files that are included from "/etc/php5/apache2/conf.d". By removing pdo.ini and pdo_mysql.ini, I stopped the attempted include of pdo.so and pdo_mysql.so. PHP now works again, yay!

Unfortunately, PDO is now completely gone. It used to show up in the phpinfo() listing along with a pdo_mysql extension, but it's just not there. Hmm...

---

### Post by drwoland on 2008-02-14
had the same problem in gutsy, looked around, found this:

[http://www.mail-archive.com/debian-bugs-closed@lists.debian.org/msg115619.html](http://www.mail-archive.com/debian-bugs-closed@lists.debian.org/msg115619.html)

It essentially says that the symbol should be loaded in pdo.so and then is referenced in pdo_mysql.so

What this means is that pdo.so has to be loaded chronologically before pdo_mysql.so. Apparently, when eating it's conf files, php/apache2 sorts pdo_mysql.ini before pdo.ini in /etc/php5/apache2/conf.d. I just did this to force it to be loaded later

```

sudo mv pdo_mysql.ini zpdo_mysql.ini 
```

And it now works fine. Cheers.

---

### Post by ntom-taylor on 2008-02-26
Hello,

My name is Tom Taylor, i am running ubuntu 7.10 

I have also had this issue just happen to me.. 
I had previously installed php with pdo, and added the pdo_mysql and pdo extension into the /etc/php5/apache2/php.ini file.

Once i then tried to install php5-mysql via apt-get php segfaulted and apache refused to restart.

With the pdo and pdo_mysql extension in php.ini i was getting the following error from /var/log/apache2/error.log.. 

PHP Warning:  Module 'PDO' already loaded in Unknown on line 0
PHP Warning:  Module 'pdo_mysql' already loaded in Unknown on line 0
/usr/sbin/apache2: symbol lookup error: /usr/lib/php5/20060613+lfs/pdo_mysql.so: undefined symbol: php_pdo_get_dbh_ce

Once i commented out the pdo extension, this got rid of the first PHP warning, and pdo is in phpinfo but no pdo drivers..

If i comment out pdo_mysql in /etc/php5/apache2/php.ini and also commented it out from /etc/php5/conf.d/pdo_mysql.ini and restarted apache then it worked.

Bottom line is, if anywhere at all you have pdo_mysql.so in any configuration, you get the error:

/usr/sbin/apache2: symbol lookup error: /usr/lib/php5/20060613+lfs/pdo_mysql.so: undefined symbol: php_pdo_get_dbh_ce

and apache fails to load.

Server version: Apache/2.2.4 (Ubuntu)

Kind regards,
Tom Taylor

---

### Post by algerion on 2008-06-17
I did exactly the same Tom Taylor did, with the same result. Which I decided was to uninstall php5-mysql using 

```
sudo apt-get remove php5-mysql
```

but to be sure I decided to uninstall pdo_mysql and pdo, so I did
```
pecl uninstall pdo_mysql
pecl uninstall pdo
```

and later I reinstalled pdo and pdo_mysql and it worked fine. I had to remove manually some extensions declarations in php.ini, but I think this is not a major problem.

---

### Post by gr8whitesavage on 2008-11-14
AFAIK this error is caused by missing mysql dev package seen here: [http://www.buggy.id.au/2007/02/19/installing-pdo-on-ubuntu/](http://www.buggy.id.au/2007/02/19/installing-pdo-on-ubuntu/)

i uninstalled pdo, pdo_mysql using pecl
ran % sudo apt-get install libmysqlclient15-dev
reinstall pdo, pdo_mysql using pecl

cheers!

---

### Post by eMarv on 2009-05-08
> **gr8whitesavage said:**
> 
i uninstalled pdo, pdo_mysql using pecl
ran % sudo apt-get install libmysqlclient15-dev
reinstall pdo, pdo_mysql using pecl

cheers!

thanks, this worked for me.

The only thing is I only uninstalled pdo_mysql and not pdo (and it still worked :).

---

