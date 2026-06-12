---
title: "were do i put my PHP files?"
date: 2008-04-03
forum: Programming Talk
---

### Post by wertyuiop408 on 2008-04-03
Installed apache, php and mysql using this guide [http://ubuntuguide.org/wiki/Ubuntu:Gutsy](http://ubuntuguide.org/wiki/Ubuntu:Gutsy)

Now i would like to know were to save my php files. Do i put them in the etc/apache2 folder.

---

### Post by heikaman on 2008-04-03
/var/www

---

### Post by Can+~ on 2008-04-03
you can change the root of the www directory with the sites-available, default file:

```
gksudo gedit /etc/apache2/sites-available/default &
```

For instance, my apache2 server is set to /www instead of /var/www

[HTML]NameVirtualHost *
<VirtualHost *>
        ServerName mydomain.org
        ServerAdmin webmaster@localhost

	DocumentRoot /www

	<Directory /www>
		Options FollowSymLinks
		AllowOverride None
	</Directory>
</VirtualHost>[/HTML]

Finally, reset the apache2

```
sudo apache2 -k restart
```

There's a lot of security issues about running your own apache2 server, which you should check on the apache2 manual page, but if it's only for testing at home, and hopefully, behind a router, then you can omit them.

---

