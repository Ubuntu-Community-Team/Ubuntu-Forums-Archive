---
title: "create a user for apache2 installation?"
date: 2011-12-27
forum: New to Ubuntu
---

### Post by styssi on 2011-12-27
Hi,

I did install an apache2 server on my ubuntu 8.04. 
```

apt-get install apache2

```
Does this mean, that the apache will be started as root user? Is this a security risk? I was logged in as root when I executed the command. Would it be better to create an extra user called apache and installing the apache server under that username?

Greetings
Styssi

---

### Post by Lars Noodén on 2011-12-27
The way the package handles it is already to run it as a non-root user. Apache starts as root to bind to port 80 (unless the port has been changed from the default) and then promptly switches over to running as the user 'www-data'.  So that is very secure unless by mistake www-data has been granted write access to any part of the system. 

You can look in [font=Courier New]/etc/apache2/envvars[/font] and [font=Courier New]/etc/apache2/apache2.conf[/font] to see how [User](http://httpd.apache.org/docs/2.3/mod/mod_unixd.html#user) and Group are set.

---

### Post by styssi on 2011-12-27
Hi Lars,

thanks for your answer.

Greetings
Styssi

---

### Post by Lars Noodén on 2011-12-27
You're welcome.  I should add, in case you want to read more, that the names of the two principles involved are "[least privilege](http://hissa.nist.gov/rbac/paper/node5.html)" and "[privilege separation](http://wiki.apache.org/httpd/PrivilegeSeparation)".

---

