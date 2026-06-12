---
title: "Joomla installtion problem"
date: 2006-11-27
forum: Programming Talk
---

### Post by robtotheb on 2006-11-27
I'm trying to set a local version on joomla on my edgy desktop.  I have "apache2 php5-mysql libapache2-mod-php5 mysql-server" all installed and have followed the wiki for setting them up.  I'm still getting  "MySQL support  	 Unavailable" on the welcome page to the Joomla install. Not sure whats missing.

---

### Post by tminuszero on 2006-11-27
I hate to ask this, but did you restart apache2? 

```
sudo apache2ctl graceful
```

Is MySQL running? Did you set up a user and access permissions?

---

### Post by robtotheb on 2006-11-27
yeah I've had MYSQL and apache running for ages.  I've developed a ruby on rails site on my setup so I'm flummoxed why Joomla can't access the MYSQL.

---

### Post by robtotheb on 2006-11-27
Solved the problem.

```
sudo gedit /etc/php5/apache2/php.ini
```
look for the line
**;extension=mysql.so**
and take away the semi-colon
[B]extension=mysql.so
[/B]
Save.

Then restart apache
```
sudo /usr/sbin/apache2ctl restart
```

Working fine now.

---

