---
title: "virtual host not working when adding more than one"
date: 2020-07-11
forum: New to Ubuntu
---

### Post by cnedas on 2020-07-11
Hello,

I have a VPS with Ubuntu 18.04 and have configured a first domain as virtual host following this tutorial:

[https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-ubuntu-18-04](https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-ubuntu-18-04)

and it worked great.

However, when I try adding a second domain as a virtual host, it won't load on my browser.

Am I missing anything?

Thanks,


C. Nedas.

---

### Post by TheFu on 2020-07-12
> **cnedas said:**
>  
Am I missing anything? 

Seems you are probably missing lots of things.  I suspect that isn't the question you really wanted help about.  ;)
Perhaps if you posted the virtual host config files and the relevant parts of log files (not the whole things!!!!!!) for the system and whatever web server you've decided to use, someone may take the time to respond?

Basically, prove you did what those instructions say to do.  It isn't that we don't believe you ... but ... er ... we don't believe you. ;)
Hopefully, it is a tiny mistake like we've all made 50 times already.  Let's hope.  There are lots of details. It is easy to miss things even after 10 yrs of doing this stuff.

BTW, we've all been there.  Just this morning I fixed something driving me nuts for about a month that was caused by a really dumb line missing from a config file.

---

### Post by TheFu on 2020-07-12
BTW, Ubuntu has a 1-command LAMP server install which sets up everything between apache, php, and mysql. All you need to do it setup the SSL virtual domain and settings.
```
sudo tasksel install lamp-server

```
Wouldn't that be easier ... if you started out that way?  I wouldn't suggest going back now. You are committed.

---

### Post by sdsurfer on 2020-07-16
Just to be clear . . . this is a **hosted** VPS, correct? As in, on a remote server, not your computer?

If so, didn't your hosting come with  management interface, like WHM, Cpanel, Plesk, anything? Most of anything you want to do you would do in there.

Did you try restarting Apache2 after adding the second host?

---

