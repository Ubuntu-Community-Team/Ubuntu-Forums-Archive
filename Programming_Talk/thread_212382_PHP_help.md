---
title: "PHP help"
date: 2006-07-09
forum: Programming Talk
---

### Post by truNWA on 2006-07-09
I think I have installed MYSQL and PHP and Apache. When i run this MYSQL test:
```

<html>
<head><title>MySQL Connection Test</title></head>

<body>
<h2>
<?php
$connection = mysql_connect( "localhost", "root", "" ) or die( "Sorry - unable to connect to MySQL");
echo( "Congratulations!!!! - you connected to MySQL");

?>
</h2>
</body></html>

```

firefox asks me to downlaod the file. any suggestions?

---

### Post by Engnome on 2006-07-09
Is it in /var/www ? Do access it with [http://127.0.0.1](http://127.0.0.1) ? file:// won't work.

---

### Post by noob_Lance on 2006-07-09
also ... make sure mysql is running and you have it set up correctly

---

### Post by gruepig on 2006-07-10
> **truNWA said:**
> firefox asks me to downlaod the file. any suggestions?

You've actually set up three things:  apache, php, and mysql.  It seems that apache (and all things network-related) is working, as you got asked to download the file.  Can you access any .php pages?  My guess, based on the error, is no.

Make sure the php module is enabled and configured.  For apache2 and php4, you should have something like:

```

$ cat /etc/apache2/mods-enabled/php4.load
  LoadModule php4_module /usr/lib/apache2/modules/libphp4.so

$ cat /etc/apache2/mods-enabled/php4.conf
  <IfModule mod_php4.c>
    AddType application/x-httpd-php .php .phtml .php3
    AddType application/x-httpd-php-source .phps
  </IfModule>

$ grep php /etc/mime.types
  application/x-httpd-php                         phtml pht php
  application/x-httpd-php-source                  phps
  application/x-httpd-php3                        php3
  application/x-httpd-php3-preprocessed           php3p
  application/x-httpd-php4                        php4

```

Then, once you have php pages serving, you can make sure that mysql (and the php-mysql interaction) is working.

Also a bit about security if your site is exposed to the Internet:  By default, the mysql root password is null; you'll want to change this ('mysqladmin -u root password').  Similarly, php doesn't have the most secure defaults; you can change these in /etc/php4/apache2/php.ini.  And make sure to keep your software up-to-date; this is easy to do and makes a huge difference.

---

### Post by truNWA on 2006-07-10
> **Engnome said:**
> Is it in /var/www ? Do access it with [http://127.0.0.1](http://127.0.0.1) ? file:// won't work.

yes

> **noob_Lance said:**
> also ... make sure mysql is running and you have it set up correctly

please tell me how to do that
> **gruepig said:**
> 
Make sure the php module is enabled and configured.  For apache2 and php4, you should have something like:

```

$ cat /etc/apache2/mods-enabled/php4.load
  LoadModule php4_module /usr/lib/apache2/modules/libphp4.so

$ cat /etc/apache2/mods-enabled/php4.conf
  <IfModule mod_php4.c>
    AddType application/x-httpd-php .php .phtml .php3
    AddType application/x-httpd-php-source .phps
  </IfModule>

$ grep php /etc/mime.types
  application/x-httpd-php                         phtml pht php
  application/x-httpd-php-source                  phps
  application/x-httpd-php3                        php3
  application/x-httpd-php3-preprocessed           php3p
  application/x-httpd-php4                        php4

```



I get a "No such Directory error for all of those"

---

### Post by l.tambiah on 2006-07-10
I would remove everthing, and start from scratch. Use the wiki page at [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP). I know this method of installing works...

---

### Post by ifokkema on 2006-07-10
> **truNWA said:**
> I get a "No such Directory error for all of those"
You've probably got apache 1.3 installed. I would carefully follow the link mentioned above.

---

