---
title: "Setting up Virtual Hosts on Ubuntu 14.04 Server"
date: 2014-05-20
forum: New to Ubuntu
---

### Post by Dave_Bailey on 2014-05-20
I am trying to set-up virtual hosts on a Ubuntu server (named 'Web-Server') on a home network and have followed all the instructions on how to set up virtual hosts.  Both my test sites (Test1 and Test2) appear in the 'sites-available' and 'sites-enabled' '/etc/apache2' directories. There are 'index.html' files in both '/var/www/Test1' and  '/var/www/Test2' directories. Apache2 has been restarted.  However, when I attempt to connect from my windows PC (running firefox), returns a 404 error.  I think I may have a basic misunderstanding here on how to address the server.  Typing in 'Web-Server' brings up just one of the test sites. Attempting to type anything like 'Web-Server/Test1' returns a 404 error.  Can someone help and put me straight on this issue.  Many thanks. Dave

---

### Post by sandyd on 2014-05-20
Can you post your virtual host configuration

Thanks.

---

### Post by Dave_Bailey on 2014-05-20
Thanks for your reply. I assume you mean the .conf files in 'sites-available' and 'sites-enabled'

Test1.conf reads as
```

<VirtualHost *:80>
	# The ServerName directive sets the request scheme, hostname and port that
	# the server uses to identify itself. This is used when creating
	# redirection URLs. In the context of virtual hosts, the ServerName
	# specifies what hostname must appear in the request's Host: header to
	# match this virtual host. For the default virtual host (this file) this
	# value is not decisive as it is used as a last resort host regardless.
	# However, you must set it for any further virtual host explicitly.
	#ServerName [www.example.com](www.example.com)


	ServerAdmin 
	ServerName Web-Server
	DocumentRoot /var/www/Test1
	ServerAlias [www.Test1.com](www.Test1.com)


	# Available loglevels: trace8, ..., trace1, debug, info, notice, warn,
	# error, crit, alert, emerg.
	# It is also possible to configure the loglevel for particular
	# modules, e.g.
	#LogLevel info ssl:warn


	ErrorLog ${APACHE_LOG_DIR}/error.log
	CustomLog ${APACHE_LOG_DIR}/access.log combined


	# For most configuration files from conf-available/, which are
	# enabled or disabled at a global level, it is possible to
	# include a line for only one particular virtual host. For example the
	# following line enables the CGI configuration for this host only
	# after it has been globally disabled with "a2disconf".
	#Include conf-available/serve-cgi-bin.conf
</VirtualHost>
```


# vim: syntax=apache ts=4 sw=4 sts=4 sr noet

Test2.conf reads as
```

<VirtualHost *:80>
	# The ServerName directive sets the request scheme, hostname and port that
	# the server uses to identify itself. This is used when creating
	# redirection URLs. In the context of virtual hosts, the ServerName
	# specifies what hostname must appear in the request's Host: header to
	# match this virtual host. For the default virtual host (this file) this
	# value is not decisive as it is used as a last resort host regardless.
	# However, you must set it for any further virtual host explicitly.
	#ServerName [www.example.com](www.example.com)


	ServerAdmin 
	ServerName Web-Server
	DocumentRoot /var/www/Test2
	ServerAlias [www.Test2.com](www.Test2.com)


	# Available loglevels: trace8, ..., trace1, debug, info, notice, warn,
	# error, crit, alert, emerg.
	# It is also possible to configure the loglevel for particular
	# modules, e.g.
	#LogLevel info ssl:warn


	ErrorLog ${APACHE_LOG_DIR}/error.log
	CustomLog ${APACHE_LOG_DIR}/access.log combined


	# For most configuration files from conf-available/, which are
	# enabled or disabled at a global level, it is possible to
	# include a line for only one particular virtual host. For example the
	# following line enables the CGI configuration for this host only
	# after it has been globally disabled with "a2disconf".
	#Include conf-available/serve-cgi-bin.conf
</VirtualHost>


# vim: syntax=apache ts=4 sw=4 sts=4 sr noet

```


directories '/var/www/Test1' and '/var/www/Test1' both have an 'index.html'

Many thanks
Dave

---

### Post by sandyd on 2014-05-20
Comment out ServerAlias and uer ServerName instead.

---

### Post by Dave_Bailey on 2014-05-20
Tried commenting out 'ServerAlias' and set 'ServerName [www.Test1.com](www.Test1.com)' is that what you meant? Have restarted apache2, but it hasn't made any difference.  What should I be typing into the URL to get say 'Test2' site.  Many thanks. Dave

---

