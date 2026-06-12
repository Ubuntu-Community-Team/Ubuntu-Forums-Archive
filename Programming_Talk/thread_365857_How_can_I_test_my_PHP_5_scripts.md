---
title: "How can I test my PHP 5 scripts?"
date: 2007-02-20
forum: Programming Talk
---

### Post by Vinze on 2007-02-20
Hey,

Until yesterday, I used [XAMPP](http://www.apachefriends.org/en/xampp-linux.html) to test my PHP scripts. However, now when I visit [http://localhost](http://localhost) , it just keeps loading until I finally get a "connection timed out" error. I tried installing the newest version but that did not help.

Then I tried [installing Apache, MySQL and PHP](https://help.ubuntu.com/community/ApacheMySQLPHP) but, apart from that [it would not start MySQL](http://forums.vpslink.com/showthread.php?t=797) and still not load [http://localhost](http://localhost) , I also had no idea where to place my files.. Aargh!

So... Any link to a guide or something on PHP testing on Ubuntu?

---

### Post by Paul41 on 2007-02-20
> I also had no idea where to place my files

For Apache your files go in /var/www

Sorry, but I am not sure what could be causing the rest of your problems.

---

### Post by Vinze on 2007-02-20
> **Paul41 said:**
> For Apache your files go in /var/www

Sorry, but I am not sure what could be causing the rest of your problems.

OK, that's already something to know...

The problem I with the installation is the same as described here: [http://forums.vpslink.com/showthread.php?t=797](http://forums.vpslink.com/showthread.php?t=797)

However, the solution there was to [quote=fransisco_athens]I too am running Edgy. Heres how I got it to work:
apt-get install mysql-server-5.0

you will get errors...
and a [fail]
(take a look at /var/log/syslog for information if you are curious)
uncomment skip-innodb in /etc/mysql/my.cnf

install mysql-server again:
apt-get install mysql-server-5.0[/quote]

However, that does not work for me :(

---

### Post by Paul41 on 2007-02-20
Have you tried this?

```
sudo apt-get -f install
```

---

### Post by Vinze on 2007-02-20
> **Paul41 said:**
> Have you tried this?

```
sudo apt-get -f install
```

I tried now, it didn't work :(

---

### Post by Flubs4u on 2007-02-21
So your problem is with installing mysql?

have you tried:
sudo dpkg-reconfigure mysql-server?

Also once you get mysql and php installed don't forget to configure the php5 mysql module since it's no longer enabled by default.

---

### Post by Koybe on 2007-02-21
You can also try :
apt-get install --reinstall mysql-server

You can also remove and purge :
apt-get --purge remove mysql-server

Maybe make sur this is not a meta-package and remove everything regarding to mysql, you can get a summary of what's install this way :
dpkg -l mysql*

Finaly retry installing...

---

### Post by Vinze on 2007-02-22
Well, I've got XAMPP running again, turns out > auto lo
iface lo inet loopbackwas missing from /etc/network/interfaces

There's no reason to try real Apache now anymore, thanks for all the replies anyways :D

---

