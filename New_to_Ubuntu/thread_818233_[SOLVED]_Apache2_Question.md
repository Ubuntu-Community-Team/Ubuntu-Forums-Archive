---
title: "[SOLVED] Apache2 Question"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by ejpyle on 2008-06-04
Ok...so here is the question..

Where do I go in Apache2 to change which file it loads by default?
Right now when someone goes to my site it goes to "index.php" and I want it to load to "home.php"

Thanks!!!

---

### Post by spiderbatdad on 2008-06-04
Check out the virtual hosts file "sites-available/default" generally points to an index.html in /var/www.

Not sure why the php page would be showing by default, unless you set that up in httpd.conf

Anyway, the config files are usually in /etc/apache2

---

### Post by ejpyle on 2008-06-04
> **spiderbatdad said:**
> Check out the virtual hosts file "sites-available/default" generally points to an index.html in /var/www.

Not sure why the php page would be showing by default, unless you set that up in httpd.conf

Anyway, the config files are usually in /etc/apache2

my HTTPD.CONF is blank. I was not sure where I was placing code to tell Apache to load a custom page rather than an index.

---

### Post by ejpyle on 2008-06-04
> **ejpyle said:**
> my HTTPD.CONF is blank. I was not sure where I was placing code to tell Apache to load a custom page rather than an index.

```
DocumentRoot /media/disk/www/
	<Directory />
		Options FollowSymLinks
		AllowOverride All
	</Directory>
	<Directory /media/disk/www/>
		Options Indexes FollowSymLinks MultiViews
		AllowOverride All
		Order allow,deny
		allow from all
	</Directory>
```

Where do I plug it in at?

---

### Post by ukripper on 2008-06-04
you have to place your index page in /var/www/

---

### Post by linux6994 on 2008-06-04
Apache2 
When you are running, /var/www is the place where all pages are displayed from. If you hit your IP address with a html request you should get "It Works!" that is the message in the appache2-default folder. You can create another in the /var/www and go to it such as [http://192.168.1.11/yourstuff/yourpage](http://192.168.1.11/yourstuff/yourpage) and you will get to your stuff.

Good Luck!

---

### Post by ejpyle on 2008-06-04
> **ukripper said:**
> you have to place your index page in /var/www/

Your missing the point...right now my document root is /media/disk/www and I have all files placed in there...

index.php
home.php
contact.php
etc etc

When someone goes to my domain index.php is what loads by default.
I want it to where it loads home.php by default.

---

### Post by theolster on 2008-06-04
This should do it:

edit the default config file```
sudo gedit /etc/apache2/sites-available/default
```then change the lines that read```
<Directory />
        Options FollowSymLinks
        AllowOverride None
</Directory>
```to```
<Directory />
        Options FollowSymLinks
        AllowOverride None
        DirectoryIndex home.php
</Directory>
```this will overwrite any of the previous directoryindex settings, so be sure to add any others you might need as well, such as home.html.

Don't forget to restart the apache server```
sudo /etc/init.d/apache2 restart 
```

---

### Post by ejpyle on 2008-06-04
> **theolster said:**
> This should do it:

edit the default config file```
sudo gedit /etc/apache2/sites-available/default
```then change the lines that read```
<Directory />
        Options FollowSymLinks
        AllowOverride None
</Directory>
```to```
<Directory />
        Options FollowSymLinks
        AllowOverride None
        DirectoryIndex home.php
</Directory>
```this will overwrite any of the previous directoryindex settings, so be sure to add any others you might need as well, such as home.html.

Don't forget to restart the apache server```
sudo /etc/init.d/apache2 restart 
```


I love you a whole bunch right now....you fixed my problem

---

