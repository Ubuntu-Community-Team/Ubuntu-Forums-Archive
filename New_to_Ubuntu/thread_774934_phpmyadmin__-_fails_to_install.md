---
title: "phpmyadmin  - fails to install"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by Swerve1000 on 2008-04-29
I am trying to install phpmyadmin as in the tutorial [here]("https://help.ubuntu.com/community/phpMyAdmin")

When I enter the command:-

> sudo apt-get install phpmyadmin

It says:-

> 7 not fully installed or removed
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory.

I don't understand this.

I'm using 8.04 server edition. It's a new install, just added Webmin and proftpd only to it so far.

Many thanks for any advice!

---

### Post by iSplicer on 2008-04-29
Try this:

sudo apt-get clean

if that doesnt work..

sudo rm /var/cache/apt/archives/lock

---

### Post by Kon.Xen on 2008-04-29
> **Swerve1000 said:**
> I am trying to install phpmyadmin as in the tutorial [here]("https://help.ubuntu.com/community/phpMyAdmin")

When I enter the command:-



It says:-



I don't understand this.

I'm using 8.04 server edition. It's a new install, just added Webmin and proftpd only to it so far.

Many thanks for any advice!

The way I understand it. "Apt" cannot find the place on the web to download from.

---

### Post by iSplicer on 2008-04-29
> **Kon.Xen said:**
> The way I understand it. "Apt" cannot find the place on the web to download from.

Wrong. If thats the case, it would have said "package not found, etc"

Try this:

sudo apt-get clean

if that doesnt work..

sudo rm /var/cache/apt/archives/lock

---

### Post by GavinZac on 2008-04-29
I usually get that error when dealing with two package systems at once, i.e. 2 of apt-get, aptitude, synaptic, add/remove or gdebi. Only one program can lock the package system at a time.

---

### Post by Swerve1000 on 2008-04-29
It worked!

Thanks a million. The first command said the same message, but the second worked straight away. phpmyadmin  config screen is now showing after the apt-get install command.

Thanks thanks thanks :)

---

