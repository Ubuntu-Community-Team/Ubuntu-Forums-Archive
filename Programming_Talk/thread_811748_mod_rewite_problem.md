---
title: "mod_rewite problem"
date: 2008-05-29
forum: Programming Talk
---

### Post by tim_bobo on 2008-05-29
With the Ubuntu 8.04 LAMP server on laptop, my mod_rewrite is working a little differently than the Fedora server we have running.  It took a while to figure this out, but I'm just wondering if there is a configuration setting to change this.

I have the following:
RewriteRule   ^signup/?$  main.php?page=signup


and I have:
signup.php

When go to [www.example.com/signup/](www.example.com/signup/), I get the signup.php....it's ignoring the file extension.

Is there a apache setting to change this?

Thanks for any help you can provide

---

### Post by angels on 2008-09-19
I have the same problem - mod_rewrite doesn't work on my localhost.
I set the virtual host as:
```
<VirtualHost *>
	ServerAdmin webmaster@localhost
	
	DocumentRoot /var/www/

	#<Directory /var/www/>
	#	Options FollowSymLinks
	#	AllowOverride None
	#</Directory>

	<Directory /var/www/>
		Options Indexes +FollowSymLinks -MultiViews
		AllowOverride All
		Order allow,deny
		Allow from all
	</Directory>

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride All
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
        AllowOverride All
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>
```

mod_rewrite is enabled, and my .htaccess looks like:

```
<IfModule mod_rewrite.c>
RewriteEngine On
RewriteBase /example

RewriteRule ^news$ http://localhost/example/index_template.php?page=news

</IfModule>
```

The RewriteRule works fine on my website and I really don't know why doesn't work here . Any ideas? I would appreciate so much :)

---

### Post by angels on 2008-09-20
sorry, I found a mistake - a very silly mistake :(
thnx anyway :)

---

