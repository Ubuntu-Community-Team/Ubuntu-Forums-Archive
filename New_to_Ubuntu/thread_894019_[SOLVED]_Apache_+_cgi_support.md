---
title: "[SOLVED] Apache + cgi support"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by Promaster91 on 2008-08-18
I have an apache web server. I have a cgi file on the server however when I access it from Firefox it shows up as a text file. How do I make it executable? Thanks.

---

### Post by kaivalagi on 2008-08-18
I assume you are running apache2? If so read on...

To have CGI running I added the following to the /etc/apache2/sites-enabled/default linked file:

```

	ScriptAlias /cgi-bin/ /home/www/cgi-bin/
	<Directory "/home/www/cgi-bin/">
		#AllowOverride None
		AllowOverride AuthConfig 
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>
```

You may want to change the paths, mine are custom. I also changed the AllowOverride so authentication is required. If you are running the defaults (/var/www/) and you don't want authentication, then it would look something like this:

```

	ScriptAlias /cgi-bin/ /usr/lib/cgi-bin
	<Directory "/usr/lib/cgi-bin">
		AllowOverride None
		Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
		Order allow,deny
		Allow from all
	</Directory>
```

The scriptalias means you can access the cgi-bin from the root of the site.

You will need to place the cgi files in the correct folder, in the case of above it is /usr/lib/cgi-bin

Edit: You may not have the cgi module enabled, to make sure run the following:

```
sudo a2enmod cgi
```

Hope that helps

---

### Post by Promaster91 on 2008-08-18
Ok I have acess to that file. However when goto the link firefox want to download the file.

---

### Post by kaivalagi on 2008-08-18
> **Promaster91 said:**
> Ok I have acess to that file. However when goto the link firefox want to download the file.

If you've done both the a2enmod call and edited the default, the only thing left is to restart apache

Run this:

```
/etc/init.d/apache2 force-reload
```

then this:

```
/etc/init.d/apache2 restart
```

fingers crossed :)

---

### Post by Promaster91 on 2008-08-18
No still the same outcome!?! :confused:

---

### Post by az on 2008-08-18
> **Promaster91 said:**
> No still the same outcome!?! :confused:

Try clearing your browser cache (reload the page with F5).

---

### Post by Promaster91 on 2008-11-08
Good News. I used this program called Xampp. It bundles Apache with cgi, ssl, ftp and some more stuff. Easy guide to install it [here]("http://geekyogi.wordpress.com/2008/06/14/xampplampp-on-ubuntu/").

---

