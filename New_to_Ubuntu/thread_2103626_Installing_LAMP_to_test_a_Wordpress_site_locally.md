---
title: "Installing LAMP to test a Wordpress site locally?"
date: 2013-01-10
forum: New to Ubuntu
---

### Post by Ranger_Joe on 2013-01-10
Hey All,
I need to install LAMP (which I've never used) and test a Wordpress site on it locally. Who knows how to do this or has done it before? 

Do I need to also install MySQL? I would imagine that I do. 

Please help. Thanks!

---

### Post by CharlesA on 2013-01-10
The lamp stack includes MySQL.

You should be able to run this:

```
sudo tasksel install lamp-server
```

---

### Post by haqking on 2013-01-10
> **Ranger_Joe said:**
> Hey All,
I need to install LAMP (which I've never used) and test a Wordpress site on it locally. Who knows how to do this or has done it before? 

Do I need to also install MySQL? I would imagine that I do. 

Please help. Thanks!

The M in LAMP means MySQL ;-) though sometimes MariaDB

[http://ubuntuserverguide.com/2012/05/how-to-install-latest-wordpress-in-ubuntu-server-12-04-lts.html]("https://*********************.com/2012/06/30/how-to-install-and-host-wordpress-on-ubuntu-12-04-lts/")

---

### Post by Cheesemill on 2013-01-10
> **CharlesA said:**
> The lamp stack includes MySQL.

You should be able to run this:

```
sudo tasksel install lamp-server
```

Or if you don't want to use tasksel you can just do...
```
sudo apt-get install lamp-server^
```

---

### Post by d4rk0wl on 2013-01-10
Yeah it really is as simple as what has been said, once it is installed the web root will be in:
```
/var/www
```

Also, not sure if you need help with createing the DB for wordpress or not but in case you do there is already a nice tutorial up on the wordpress site about how to do it. Helped me out a lot when I was learning SQL. [(HERE)]("http://codex.wordpress.org/Installing_WordPress#Using_the_MySQL_Client").

Regards,
- D4rk0wl

---

