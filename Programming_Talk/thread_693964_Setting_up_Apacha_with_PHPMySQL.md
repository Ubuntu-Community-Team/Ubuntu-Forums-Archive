---
title: "Setting up Apacha with PHP/MySQL"
date: 2008-02-11
forum: Programming Talk
---

### Post by happysmileman on 2008-02-11
I'd like to set up Apache with MySQL and PHP on Gutsy, I can find the packages fine, but on any other release of (K)ubuntu I've installed (6.06 ,6.10, 7.04) I've had trouble installing it, usually either PHP just wouldn't be recognised by Apache or MySQL wouldn't be recognised by MySQL, usually because they had to be installed in a certain order I couldn't find. This time I'm asking before I get a chance to cause myself any hassle.

My question is: How do I install them?

After that, I'd like to be able to set them up locally, using my user account, I don't need to worry about permissions  or security much since it'll all be made locally and not accessable to anyone from the outside world (once site works I might upload it to a webhost though).

So would giving myself ownership of the "/var/www/" or whatever workj, then I can just symlink it to a plave in my /home? Or is there an easy way to change the default directory for the site? (for example changing /var/www/ in some config file to /home/paul/www/) This'd probably be less hacky

---

### Post by aks44 on 2008-02-11
```
sudo tasksel
```

Check "LAMP Server" and be sure **not** to uncheck anything[COLOR="DimGray"] (some people screwed up their system by mindlessly "experimenting" with the other choices)[/COLOR].

I'd advise you to keep the [http://localhost/](http://localhost/) directory (aka. /var/www/) clean from PHP files, and symlink from /var/www/whatever/ to ~/www/whatever/. At least phpMyAdmin uses that symlink method (both on Ubuntu and Debian).

---

### Post by melopsittacus on 2008-02-11
Hi! I think you first have to install mysql and php and finally apache. Than you should configure apache to use php: in the /etc/apache2/mods-enabled/ directory you should have two files called php5.conf and php5.load with the following contents:

php5.conf:
```

<IfModule mod_php5.c>
  AddType application/x-httpd-php .php .phtml .php3
  AddType application/x-httpd-php-source .phps
</IfModule>

```

php5.load:
```
LoadModule php5_module /usr/lib/apache2/modules/libphp5.so

```

In order to change the webroot directory, you have to edit the file /etc/apache2/sites-available/default changing the DocumentRoot to the path where your webroot is.

Finally, in the file /etc/php5/apache2/php.ini you should enable MySQL by uncommenting the line ```
extension=mysql.so

```

---

### Post by happysmileman on 2008-02-11
> **aks44 said:**
> ```
sudo tasksel
```

Check "LAMP Server" and be sure **not** to uncheck anything[COLOR="DimGray"] (some people screwed up their system by mindlessly "experimenting" with the other choices)[/COLOR].

Never even heard of tasksel before, seems VERY useful. :P

> I'd advise you to keep the [http://localhost/](http://localhost/) directory (aka. /var/www/) clean from PHP files, and symlink from /var/www/whatever/ to ~/www/whatever/. At least phpMyAdmin uses that symlink method (both on Ubuntu and Debian).

Ok cool, shall try that, so that means that I make the site in "~/www/site", symlink "/var/www/site/" to it, and the site would be "http://localhost/site/" I assume, whereas "http://localhost/" would just be a list of the directorys?

---

### Post by aks44 on 2008-02-12
> **happysmileman said:**
> Ok cool, shall try that, so that means that I make the site in "~/www/site", symlink "/var/www/site/" to it, and the site would be "http://localhost/site/" I assume

Exactly.

> **happysmileman said:**
> whereas "http://localhost/" would just be a list of the directorys?

Using Apache's default configuration, yes. There are options to stop Apache from generating that list though, if you really want/need to.

---

