---
title: "no localhost root location"
date: 2014-10-16
forum: New to Ubuntu
---

### Post by prasanna6 on 2014-10-16
I installed apache2, mysql, php and phpmyadmin . The root location is in var/www now but i wanted to change it to something like /home/user/sites or something. In the other threads , the solution was adding some code in the 000-default.conf file in sites-enabled folder , but there is no such file in my folder, infact there is no file in /etc/apache2/stres-enabled folder. So how do i change the location now?

---

### Post by IAmJ on 2014-10-16
Kindly execute this command 
 dpkg --get-selections | grep apache 
or which apache2
to check if your apache is correctly installed

---

### Post by cariboo on 2014-10-16
You should have a file called:

```
000-default
```

in /etc/apache2/sites-enabled. that is a symbolic link to /etc/apache2/sites-available/default.

The contents of default should look something like this:

```
cat default
<VirtualHost *:80>
	ServerAdmin webmaster@localhost

	DocumentRoot /var/www
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

	ErrorLog ${APACHE_LOG_DIR}/error.log

	# Possible values include: debug, info, notice, warn, error, crit,
	# alert, emerg.
	LogLevel warn

	CustomLog ${APACHE_LOG_DIR}/access.log combined

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

You can set the home directory, by editing the DocumentRoot entries.

---

