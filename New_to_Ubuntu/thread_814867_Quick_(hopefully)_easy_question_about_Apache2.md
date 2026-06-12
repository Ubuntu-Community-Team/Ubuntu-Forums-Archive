---
title: "Quick (hopefully) easy question about Apache2"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by JameoPotato on 2008-06-01
Hi,
So to simply put it I am getting the default, "apache2: Could not reliably determine the server's fully qualified domain name..." at the starting of apache2.

BUT the funny thing is... my web server is fully operational and everything is working just as I had hoped. 
(i can browse to my website and it works fine)

I am just annoyed by that little error message at the start of apache2.

I think it is my hosts file or sites-available file which I have attached to help find the problem.

/etc/hosts:
```
127.0.0.1	localhost
127.0.1.1	ubuntuserver

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

/etc/apache2/sites-available/jameopotato:
```
<VirtualHost *:80>
	ServerAdmin someone@somewhere.com
	ServerName jameopotato.com
	ServerAlias www.jameopotato.com
	ServerSignature On
	DocumentRoot /var/www/jameopotato
	<Directory />
		Options FollowSymLinks
		AllowOverride None
	</Directory>
	<Directory /var/www/jameopotato>
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

/etc/apache2/httpd.conf:
```
NameVirtualHost *:80
<VirtualHost *:80>
	ServerAdmin someone@somewhere.com
	ServerName jameopotato.com
	ServerAlias www.jameopotato.com
	DocumentRoot /var/www/jameopotato	
</VirtualHost>

```

And yes I have a2ensite jameopotato and restarted apache2...

Thanks in advance.

---

### Post by quelx on 2008-06-01
Edit your **/etc/hosts** file. On the same line, after **localhost** put your domain name, eg. *ubuntuforums.org*.

```
127.0.0.1	localhost myfullyqualifieddomain.org
```

---

### Post by JameoPotato on 2008-06-01
hmm didn't seem to change anything. I still get the message at apache2 restart.

---

### Post by rraj.be on 2008-06-01
Just try re installation of apache.

many such problems might be a result of bad installation or misconfiguration

---

### Post by quelx on 2008-06-01
out of curiosity does **hostname -f** show anything on the server, don't really want to know what it shows, just if anything pops out.

---

