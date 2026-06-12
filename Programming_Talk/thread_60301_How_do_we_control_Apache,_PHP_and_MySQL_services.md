---
title: "How do we control Apache, PHP and MySQL services???"
date: 2005-08-27
forum: Programming Talk
---

### Post by ROUBOS on 2005-08-27
Hi,
I'm learning PHP and MySQL with Apache Web server.
So I just installed Apache 2, MySQL (including the contro center) and PHP4 from the repositories. (followed ubuntuguide).

Eveyrhing seems to be working fine. My PHP test page is loading on [http://localhost/](http://localhost/)
so it should be sweet.

I just wanted to ask, how do we control these services? Do we start apache.. MySQL etc? Is it always on now that it's installed?

---

### Post by Brian Puccio on 2005-08-27
If you installed the software from the ubuntu packages, yes, they will start upon boot. There's a few ways to do what you ask

sudo /etc/init.d/apache2 stop
sudo /etc/init.d/apache2 start
sudo /etc/init.d/mysql stop
sudo /etc/init.d/mysql start

There's also the apache2ctl that can be used (don't forget to sudo on that as well).

---

### Post by sto6ma9ch on 2005-08-27
Usually controlling services is a matter of issuing one of the following commands
```
sudo /etc/init.d/name_of_service stop
```
```
sudo /etc/init.d/name_of_service start
```
```
sudo /etc/init.d/name_of_service restart
``` 
Just replace "name_of_service" with "mysql" or "apache".
PHP is used in conjunction with Apache, so there isn't (as far as I know) a separate PHP service. If you make changes to your PHP setup, you'll need to restart Apache.
Installing Apache and MySQL will create startup entries in the /etc/rc<runlevel>.d directories. For more info on Linux runlevels, go here 
[http://64.233.167.104/search?q=cache:Xl_xNLNgjL4J:www.debian-administration.org/articles/212+debian+runlevels&hl=en](http://64.233.167.104/search?q=cache:Xl_xNLNgjL4J:www.debian-administration.org/articles/212+debian+runlevels&hl=en)
You can check what's being started at boot by issuing the following command
```
dmesg
```
Among other things, there will be a list of services started. To change services starting automatically at boot, you can use the "update-rc.d" command. More info on this can be found in it's man page.

---

