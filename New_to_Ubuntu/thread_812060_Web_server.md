---
title: "Web server"
date: 2008-05-29
forum: New to Ubuntu
---

### Post by Pap3r on 2008-05-29
So I just recently delved into the web server realm and attempted to set up a web server.

It works well, it's a LAMP server and I can view it form machines on my network.  I'd like to view it from machines outside my network too, but I'm not completely sure how to do that.  I have set up a virtual host like this: ```
pap3r|UBox~| cat /etc/apache2/httpd.conf
 <VirtualHost xxx.xxx.xxx.xxx>
     ServerName MyServer
     DocumentRoot /var/www/
  </Virtualhost>

# ServerName is to be specified to avoid warning during reload
ServerName MyServer

```

I'm not sure if I did it right, and I'm not sure what else I would have to do.  I have googled endlessly, but I'm unable to find my specific answer.  After "<Virtual Host" I put my internet IP, assuming that would allow people to access my site remotely.  However, when I go to my internet IP, it leads to my router... from inside my network.  I'm not sure if that's normal, as I've never tried before.  However, it doesn't outside my network, which is good.  I had a friend test it for me.

What am I supposed to do?  I'm reallly new to setting up this apache server.

---

### Post by edd07 on 2008-05-29
If that IP leads to your router, I think you have to setup the router so it forwards the HTTP port (I think its port 80) to your server. How you do that depends on the router.

Hope this helps

---

### Post by Pap3r on 2008-05-29
I have forwarded the port already :(  That's why I'm wondering.

---

### Post by spiderbatdad on 2008-05-29
ServerName in httpd.conf should be:

ServerName localhost
ServerName <your public ip> as found at [www.whatismyip.com](www.whatismyip.com)

Then browse to the page by typing your ip address into the address bar of your browser.
to use a name, you must register with a dns service like DYNDNS.

[http://spiderbatdad.wordpress.com/basic-apache2-how-to/](http://spiderbatdad.wordpress.com/basic-apache2-how-to/)

---

### Post by Pap3r on 2008-05-29
I changed the httpd to ```
 <VirtualHost 70.16.102.83>
     ServerName localhost
     DocumentRoot /var/www/
  </Virtualhost>

# ServerName is to be specified to avoid warning during reload
ServerName localhost

```

But I have a feeling that's not what you meant.

---

### Post by tigerplug on 2008-05-29
> **Pap3r said:**
> So I just recently delved into the web server realm and attempted to set up a web server.

It works well, it's a LAMP server and I can view it form machines on my network.  I'd like to view it from machines outside my network too, but I'm not completely sure how to do that.  I have set up a virtual host like this: ```
pap3r|UBox~| cat /etc/apache2/httpd.conf
 <VirtualHost xxx.xxx.xxx.xxx>
     ServerName MyServer
     DocumentRoot /var/www/
  </Virtualhost>

# ServerName is to be specified to avoid warning during reload
ServerName MyServer

```

I'm not sure if I did it right, and I'm not sure what else I would have to do.  I have googled endlessly, but I'm unable to find my specific answer.  After "<Virtual Host" I put my internet IP, assuming that would allow people to access my site remotely.  However, when I go to my internet IP, it leads to my router... from inside my network.  I'm not sure if that's normal, as I've never tried before.  However, it doesn't outside my network, which is good.  I had a friend test it for me.

What am I supposed to do?  I'm reallly new to setting up this apache server.



Worth taking a look here:
[http://articles.slicehost.com/](http://articles.slicehost.com/)

Thats where I learned about it.

Any questions on that stuff feel free to let me know ;)

---

### Post by spiderbatdad on 2008-05-29
The link I provided above gives a basic step by step on the procedure I follow, using some graphical interfaces, as well:[http://spiderbatdad.wordpress.com/basic-apache2-how-to/](http://spiderbatdad.wordpress.com/basic-apache2-how-to/)

---

### Post by Pap3r on 2008-05-29
That was a lot of nice information, but when I enter the IP it still can't access my site.  It accesses my router. I changed my httpd to only display ```
ServerName localhost

ServerName 70.16.102.83
```
and my sites-available, I added mysite, but when I attempted to disable sites-available/default, it said default didn't exist...  Even though it does.

This is my mysite ```
NameVirtualHost localhost
<VirtualHost 70.16.102.83>
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
```

---

### Post by spiderbatdad on 2008-05-29
```
NameVirtualHost localhost
<VirtualHost 70.16.102.83>

```

Change to:

```
NameVirtualHost *
<VirtualHost *>
```

Httpd.conf"

```
ServerName localhost
ServerName 70.16.102.83
```

Did you give the complete path to disable the default site?

sudo a2dissite /etc/apache2/sites-available/default
sudo a2ensite /etc/apache2/sites-available/mysite


Also check: /etc/apache2/ports.conf

```
Listen 80

<IfModule mod_ssl.c>
    Listen 443
</IfModule>
```

Note: disabling the defualt site requires you to have something, either index.html or files with indexing enabled in the directory options, to be able to browse to. Or you could copy the default index.html from /var/www to your my_www folder in your home directory.

---

