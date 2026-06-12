---
title: "Local dev environment for apache virtual hosts"
date: 2015-04-26
forum: New to Ubuntu
---

### Post by r3bol on 2015-04-26
Hi, I successfully setup a virtual host from /etc/www

I tried the same thing with another host, but this time pointed the host to a dev folder in home/user. When trying to access the index.html in the browser, the result was an error: 403 Forbidden. 

Steps: 

In /etc/hosts I added ci.test to the file...

```
127.0.0.1	localhost
127.0.1.1	Aspire
127.0.0.1	ci.test
127.0.0.1	test.com

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
```

In /etc/apache2/sites-available I created ci.conf

```
<VirtualHost *:80>
	
	ServerName www.ci.test
	ServerAlias ci.test
	
	ServerAdmin webmaster@localhost
	DocumentRoot /home/leke/www/ci

	#LogLevel info ssl:warn
	ErrorLog ${APACHE_LOG_DIR}/error.log
	CustomLog ${APACHE_LOG_DIR}/access.log combined
	#Include conf-available/serve-cgi-bin.conf

</VirtualHost>

# vim: syntax=apache ts=4 sw=4 sts=4 sr noet


```

Then did sudo a2ensite ci.conf which created a copy in /etc/apache2/sites-enabled

Finally I reloaded apache as instructed. 

Does anyone know why this happens?

---

### Post by Holger_Gehrke on 2015-04-26
Looks like a permission problem to me. Apache runs as user 'www-data' and is not member of any group but 'www-data', so it can not read data that's not either world-readable or chown-ed or chgrp-ed to it. Check the permission on the directory and on the files inside it.

---

### Post by r3bol on 2015-04-26
> **Holger_Gehrke said:**
> Looks like a permission problem to me. Apache runs as user 'www-data' and is not member of any group but 'www-data', so it can not read data that's not either world-readable or chown-ed or chgrp-ed to it. Check the permission on the directory and on the files inside it.

I tried the following but no luck...

cd ~/leke
sudo chown www-data:leke www
sudo chown www-data:www-data www

ls -l 
drwxrwxr-x 4 www-data www-data 4096 huhti 26 20:51 www

---

### Post by r3bol on 2015-04-26
I was wondering, would it be a security risk if I changed ownership of a folder inside /var/www ?

So for example...

cd /var/www
sudo chown leke:leke test 

Then I could work on the files quite easily without permission problems.

---

### Post by Holger_Gehrke on 2015-04-26
Well, DocumentRoot is set to "/home/leke/www/ci", what are the permissions on that ? I'd just do```

chgrp -R www-data /home/leke/www/
chmod -R g+r-w-x /home/leke/www/

```
(the '-R' option stands for "recursive") and then give execute permission on the directories to the group. If you're running / developing server side scripts, you might need to give write permission on the files that will get written to to the group on a case by case basis.

Changing ownership for '/var/www/whatever' would just give you the same problem in a different place.

I've had similar problems using mod_userdir (this gives you [http://localhost/~username/](http://localhost/~username/) for /home/username/public_html) and it was always a matter of getting the permissions just right ...

---

### Post by bab1 on 2015-04-26
> **r3bol said:**
> I was wondering, would it be a security risk if I changed ownership of a folder inside /var/www ?

So for example...

cd /var/www
sudo chown leke:leke test 

Then I could work on the files quite easily without permission problems.

A couple of points to think about.  You need to give the proper permissions (what ever they may be) all along the path.  You do not need to have the files in any particular place in the file system hierarchy. 

With the above in mind, I place all the document roots for my virtual hosts at```
/srv/data/www
```
The ownership I set is root:users all the way to doc roots (/srv/data/www).  The permissions are set at 2775 at /srv so all the data created after that always has the ownership of <some-user>:users with the permissions of 2775 for directories and 0664 for files.  Since the directories are open to all users to view and the files are world readable the pages are served.  You place the mortal users on the system in the group users.  They have read and write abilities.

In my mind I don't see this as a problem with world readable static files.  What the Apache server runs as is not important to me as the static files are accessible.

[COLOR="#0000FF"]Edit:  You can share the /srv/data/www directory with Samba or export it with NFSv4 so remote users have access.[/COLOR]

---

### Post by r3bol on 2015-04-27
I think I found an easier solution for local development. I discovered php has a built in web server and it works pretty sweet. I just cd into the dev directory I'm working on, then launch the server from the command line (specifying a different localhost port than apache uses).

---

