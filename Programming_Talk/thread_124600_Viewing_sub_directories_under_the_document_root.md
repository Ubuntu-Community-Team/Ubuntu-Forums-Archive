---
title: "Viewing sub directories under the document root"
date: 2006-02-01
forum: Programming Talk
---

### Post by DonQuixote on 2006-02-01
Alright, I'm moving to Ubuntu Linux, have Apache2 installed and running, sucessfully changed the document root and can see all the files and directories in THAT directory.

My document root directory structure:
```

/www
  phpinfo.php
  ajax/
    ch02/
      images/
      window.htm
      window.css

```
If I click on a link "ajax/" I then get the "Parent Directory" link which, of course takes me back to the document root.  But, I don't see the directory "ch02".

If I enter the address "http://localhost/ajax/ch02" I get a "403 Forbidden" error.

I have been looking in the "default" file under /etc/apache2/sites-available/ directory and fussing with some of those settings.

Here it is, if someone can tell me if this is even the correct file, and if it is what needs to change to make sub directories display the files and directories:

```

NameVirtualHost *
<VirtualHost *>
	ServerAdmin webmaster@localhost
	
	DocumentRoot /www/
	<Directory />
		Options All
		AllowOverride None
		Order allow,deny
		allow from all
	</Directory>

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options ExecCGI -MultiViews +SymLinksIfOwnerMatch
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

Thanks!

---

### Post by DonQuixote on 2006-02-01
Bloody permissions....needs 755

---

