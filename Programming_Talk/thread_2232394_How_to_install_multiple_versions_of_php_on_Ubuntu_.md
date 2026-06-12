---
title: "How to install multiple versions of php on Ubuntu 14.04"
date: 2014-07-01
forum: Programming Talk
---

### Post by denisOgr on 2014-07-01
Hi
I used this [documentation]("http://dbforch.wordpress.com/2010/05/21/apache2-fastcgi-multiple-php-versions-ubuntulucid-10-04/")(phpfarm+fastCGI), but when I want to check my version 
```
ubuntu-denis@ubuntu-denis:/etc/php/phpfarm/inst/php-5.3.27/bin$ php-cgi -v
```
I get my current version php
```
PHP 5.5.9-1ubuntu4.2 (cgi-fcgi) (built: Jun 25 2014 17:18:45)
Copyright (c) 1997-2014 The PHP Group
Zend Engine v2.5.0, Copyright (c) 1998-2014 Zend Technologies
    with Zend OPcache v7.0.3, Copyright (c) 1999-2014, by Zend Technologies
    with Xdebug v2.2.3, Copyright (c) 2002-2013, by Derick Rethans
```

My log file:
........
Generating phar.php
Generating phar.phar
PEAR package PHP_Archive not installed: generated phar will require PHP's phar extension be enabled.
clicommand.inc
pharcommand.inc
invertedregexiterator.inc
directorytreeiterator.inc
directorygraphiterator.inc
phar.inc


Build complete.
Don't forget to run 'make test'.


Installing PHP SAPI module:       cgi
Installing PHP CGI binary: /etc/php/phpfarm/inst/php-5.3.27/bin/
Installing PHP CLI binary:        /etc/php/phpfarm/inst/php-5.3.27/bin/
Installing PHP CLI man page:      /etc/php/phpfarm/inst/php-5.3.27/man/man1/
Installing shared extensions:     /etc/php/phpfarm/inst/php-5.3.27/lib/php/extensions/debug-non-zts-20090626/
Installing build environment:     /etc/php/phpfarm/inst/php-5.3.27/lib/php/build/
Installing header files:          /etc/php/phpfarm/inst/php-5.3.27/include/php/
Installing helper programs:       /etc/php/phpfarm/inst/php-5.3.27/bin/
  program: phpize
  program: php-config
Installing man pages:             /etc/php/phpfarm/inst/php-5.3.27/man/man1/
  page: phpize.1
  page: php-config.1
/etc/php/phpfarm/src/php-5.3.27/build/shtool install -c ext/phar/phar.phar /etc/php/phpfarm/inst/php-5.3.27/bin
ln -s -f /etc/php/phpfarm/inst/php-5.3.27/bin/phar.phar /etc/php/phpfarm/inst/php-5.3.27/bin/phar
Installing PDO headers:          /etc/php/phpfarm/inst/php-5.3.27/include/php/ext/pdo/
--2014-07-02 00:07:40--  [http://pear2.php.net/pyrus.phar](http://pear2.php.net/pyrus.phar)
Resolving pear2.php.net (pear2.php.net)... 5.77.39.20
Connecting to pear2.php.net (pear2.php.net)|5.77.39.20|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 10574182 (10M) [application/octet-stream]
Saving to: &#8216;/etc/php/phpfarm/src/bzips/pyrus.phar&#8217;


100%[==========================================================================================================================================================================>] 10 574 182  5,09MB/s   in 2,0s   


2014-07-02 00:07:42 (5,09 MB/s) - &#8216;/etc/php/phpfarm/src/bzips/pyrus.phar&#8217; saved [10574182/10574182]


Pyrus version 2.0.0a4 SHA-1: 72271D92C3AA1FA96DF9606CD538868544609A52
Using PEAR installation found at /etc/php/phpfarm/inst/php-5.3.27/pear
Setting php_prefix in system paths




What problem? Please help, I am tormented by this for a second day.

---

### Post by SeijiSensei on 2014-07-01
```
ubuntu-denis@ubuntu-denis:/etc/php/phpfarm/inst/php-5.3.27/bin$ php-cgi -v
```

You cannot run a binary from the directory in which its located without prefixing it with "./".  So your command will invoke the copy of php-cgi in your path, the older one.  What do you see if you type "./php-cgi -v"?

---

### Post by denisOgr on 2014-07-02
> **SeijiSensei said:**
> ```
ubuntu-denis@ubuntu-denis:/etc/php/phpfarm/inst/php-5.3.27/bin$ php-cgi -v
```

You cannot run a binary from the directory in which its located without prefixing it with "./".  So your command will invoke the copy of php-cgi in your path, the older one.  What do you see if you type "./php-cgi -v"?

5.3
Thanks!!

But now I have another problem. 
I get [COLOR=#000000][FONT=Times New Roman]**The requested URL /php-fcgi/php-cgi-5.3.27/index.php was not found on this server**.[/FONT][/COLOR] when I want to see [http://example.com/](http://example.com/) index.php
When I tried to view html file in this dir I saw this file excellent.

My **/etc/apache2/sites-enabled/example.com.conf**

```
<VirtualHost *:80>
    ServerAdmin [EMAIL="admin@example.com"]admin@example.com[/EMAIL]
    ServerName example.com
    ServerAlias [www.example.com]("http://www.example.com")
    DocumentRoot /var/www/example.com/public_html/
    <Directory "/var/www/example.com/public_html/">
        AddHandler php-cgi .php
        Action php-cgi /php-fcgi/php-cgi-5.3.27
  </Directory>
</VirtualHost>
```

**/var/www/cgi-bin/php-cgi-5.2.13**
```
#!/bin/sh
# you can change the PHP version here.
version="5.3.27"
# php.ini file location, */php-5.3.27/lib equals */php-5.3.27/lib/php.ini.
PHPRC=/etc/php/phpfarm/inst/php-${version}/lib/php.ini
export PHPRC


PHP_FCGI_CHILDREN=3
export PHP_FCGI_CHILDREN


PHP_FCGI_MAX_REQUESTS=5000
export PHP_FCGI_MAX_REQUESTS


# which php-cgi binary to execute
exec /etc/php/phpfarm/inst/php-${version}/bin/php-cgi

```

In **/etc/apache2/apache2.conf  **I add in last line:
```
# include FastCGI conf
Include /etc/apache2/php-fastcgi-.conf
```

**/etc/apache2/php-fastcgi-.conf**
```
# /php-fcgi/php-cgi-5.3.2 will be the same as /var/www/cgi-bin/ or which directory
# you choose (or perhaps change) to load the shell scripts.


# comment this out to load the PHP application statically.
#FastCgiServer /var/www/cgi-bin/php-cgi-5.2.13
#FastCgiServer /var/www/cgi-bin/php-cgi-5.3.2
ScriptAlias /php-fcgi/ /var/www/cgi-bin/

```

**/etc/apache2/mods-enabled/fastcgi.conf**
```
<IfModule mod_fastcgi>
    FastCgiWrapper /usr/lib/apache2.2.22/bin/suexec
    FastCgiConfig -idle-timeout 110 -killInterval 120 -pass-header
        HTTP_AUTHORIZATION -autoUpdate
 
    FastCgiIpcDir /var/lib/apache2/fastcgi
</IfModule>

```

Where is error?:confused:

---

### Post by SeijiSensei on 2014-07-02
```

    <Directory "/var/www/example.com/public_html/">
        AddHandler php-cgi .php
        Action php-cgi /php-fcgi/php-cgi-5.3.27
  </Directory>

```

Is the path to php-cgi-5.3.27 correct?  That points to a php-fcgi directory off the root of the file system, like /home or /var.  Is that really where it is, or is it somewhere like /etc/php/phpfarm/inst/php-5.3.27/bin/?

---

