---
title: "moodle installation"
date: 2012-02-01
forum: New to Ubuntu
---

### Post by mfreitas on 2012-02-01
Hi

It's my first time Ubuntu and moodle installation and I'm having problems with it.

I'm running an Ubuntu 11.10 LAMP server which has all the necessary components correctly installed; Apache 2.2.20, MySql 5.1.58, PHP 5.3.6-13ubuntu3.3, phpmyadmin, and everything seems to me working fine.

I've installed moodle using the "sudo apt-get install moodle" command and everything installed without errors. The database was created in MySql, it's still empty and the URL for default is

[http://localhost/moodle](http://localhost/moodle)

Affter installing it, I have checked the "/var/www" dir and there isn't any moodle directory and if I open a browser with that URL I get an error message,

Not Found
The requested URL /moodle was not found on this server.
Apache/2.2.20 (Ubuntu) Server at 192.168.10.232 Port 80

How can I fix this and make moodle work.

Thanks in advance

Miguel

---

### Post by lechien73 on 2012-02-01
The instructions seem vague...if you're just using it for your local network, then I'd suggest:

```
sudo ln -s /usr/share/moodle /var/www/moodle
```

---

### Post by mfreitas on 2012-02-01
Thanks for the reply, in future we'll open the moodle site to the public. I guess this could represent a security problem, or am i wrong?

---

### Post by lechien73 on 2012-02-01
If it's for general use, then I'd suggest following the instructions further down in the moodle installation wiki & create an apache site it /etc/apache2/sites-available & then enable it.

The symlink works, but you will be fine tune the config better by creating a site.

---

