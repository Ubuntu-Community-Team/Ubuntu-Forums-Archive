---
title: "unable to get into Gnome login screen on first boot after upgrade on warty"
date: 2005-02-14
forum: Repositories &amp; Backports
---

### Post by trinoo on 2005-02-14
i have added extra repositories as below and did an update, upgrade as well as dist-upgrade, now during 1st boot it won't get into login screen but hung in a brown screen. keyboard and mouse hung too. I have to press restart then will get into login screen on  :(


deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted 
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted 

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main

deb [http://ubuntu-bp.sourceforge.net/ubuntu/](http://ubuntu-bp.sourceforge.net/ubuntu/) warty-backports main universe

---

### Post by rudiz on 2005-02-19
You are missing a line in your repo: the main restricted of ubuntu.

Take a look in [http://ubuntuguide](http://ubuntuguide) org

---

