---
title: "000-default Apache2 config file"
date: 2008-01-09
forum: Programming Talk
---

### Post by achron on 2008-01-09
DOH!

Could some kind soul please post a vanilla (nothing altered) version of their 7.10 Ubuntu file from their Apache2 sites-enabled folder?

000-default was mistakenly deleted by a bonehead (read me) while attempting to tinker with the server and manage 3 concurrent IM discussion sessions in the office on totally different topics (they were all really work related).

Thanks in advance.

---

### Post by mlind on 2008-01-09
> **achron said:**
> DOH!

Could some kind soul please post a vanilla (nothing altered) version of their 7.10 Ubuntu file from their Apache2 sites-enabled folder?

000-default was mistakenly deleted by a bonehead (read me) while attempting to tinker with the server and manage 3 concurrent IM discussion sessions in the office on totally different topics (they were all really work related).

Thanks in advance.

You can get it from the apache2.2-common binary package.

```

cd /tmp
aptitude download apache2.2-common
dpkg -x apache2.2-common*.deb test
cp /tmp/test/etc/apache2/sites-available/default /etc/apache2/sites-available/default
sudo a2ensite default

```


Here are the file contents though
```

NameVirtualHost *
<VirtualHost *>
	ServerAdmin webmaster@localhost
	
	DocumentRoot /var/www/
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride None
		Order allow,deny
		allow from all
		# This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                #RedirectMatch ^/$ /apache2-default/
	</Directory>

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>

	ErrorLog /var/log/apache2/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog /var/log/apache2/access.log combined
	ServerSignature On

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

```

---

### Post by achron on 2008-01-10
New to Linux... new to managing my own Apache...

You offer not only a fish, but a lesson about fishing as well.

Thank you!

---

### Post by mysoogal on 2009-04-22
thanks for the  > 000-default Apache2 config file  

u saved me :lolflag:

---

### Post by RgrJim on 2009-08-30
Thanks for the post, you helped me resolve several stupid errors I made in setting up my first (and second) web sites!

:popcorn:

---

### Post by adrenalin6 on 2009-10-16
> **mlind said:**
> You can get it from the apache2.2-common binary package.

```

cd /tmp
aptitude download apache2.2-common
dpkg -x apache2.2-common*.deb test
cp /tmp/test/etc/apache2/sites-available/default /etc/apache2/sites-available/default
sudo a2ensite default

```
Here are the file contents though
```

NameVirtualHost *
<VirtualHost *>
    ServerAdmin webmaster@localhost
    
    DocumentRoot /var/www/
    <Directory />
        Options FollowSymLinks
        AllowOverride None
    </Directory>
    <Directory /var/www/>
        Options Indexes FollowSymLinks MultiViews
        AllowOverride None
        Order allow,deny
        allow from all
        # This directive allows us to have apache2's default start page
                # in /apache2-default/, but still have / go to the right place
                #RedirectMatch ^/$ /apache2-default/
    </Directory>

    ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
    <Directory "/usr/lib/cgi-bin">
        AllowOverride None
        Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
        Order allow,deny
        Allow from all
    </Directory>

    ErrorLog /var/log/apache2/error.log

    # Possible values include: debug, info, notice, warn, error, crit,
    # alert, emerg.
    LogLevel warn

    CustomLog /var/log/apache2/access.log combined
    ServerSignature On

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>

```

You saved me, thank you so much! :)

---

### Post by PicklePumpers on 2010-09-06
I had kind of the opposite problem. I'm using webmin to try to admin a test server so I created a new virtual server, that worked fine, then I deleted the "default" server in webmin but it left the 000-default file. This made apache2 very, very angry.

I was actually afraid to delete the file reading the posts here but if you have setup your own virtual host and it's in the sites-enabled then you can delete 000-default no problem. Wish webmin was better...

---

### Post by James78 on 2010-09-06
> **PicklePumpers said:**
> I had kind of the opposite problem. I'm using webmin to try to admin a test server so I created a new virtual server, that worked fine, then I deleted the "default" server in webmin but it left the 000-default file. This made apache2 very, very angry.

I was actually afraid to delete the file reading the posts here but if you have setup your own virtual host and it's in the sites-enabled then you can delete 000-default no problem. Wish webmin was better...
Just so you know, you **can** change the default server for your IP in Virtualmin, so it won't ask for 000-default. ;)

---

### Post by slavik on 2010-09-06
> **achron said:**
> New to Linux... new to managing my own Apache...

You offer not only a fish, but a lesson about fishing as well.

Thank you!
we have lost our monopoly on fish :(

---

### Post by multimedia2012 on 2012-12-29
i need the whole folder /etc/apache2 as mines all gone wrong also i need to have the root on another drive thats not my system drive for example /media/drivename/lo_web_server/www/

---

### Post by howefield on 2012-12-29
Old thread closed.

---

