---
title: "[SOLVED] How to change the group of the packages (what is the command)?"
date: 2008-09-01
forum: New to Ubuntu
---

### Post by bhadotia on 2008-09-01
Hi guys.
Alright, I will be very straight forward:
The thing is that I reinstalled ubuntu today coz I experimently installed it on xfs last time and I kept losing data due to the poor journaling capability of xfs. So what I did was I backed up all the archives I had in /var/cache/apt/archives and after the installation copied them back to that directory. The idea was that apt-get will not waste time downloading packages coz it will find them already there in the cache. But it did not work at first as apt-get was downloading packages although I had copied them to cache. The internet speed in my university is very slow today and I don't want to wait till tommorow evening to install  the packages.
So I tried to find out what was wrong and when I browsed to the cache directory using nautilus found that all the package files that I had copied had a 'unreadable' emblem over them (the one with a crossed square in an orange circle). This indicated that something was wrong. I checked the permissions tab of the nautilus properties window of the packages and found that they belonged to group 'root' where as all other .deb files that I download from internet belong to group 'plugdev'. So I guess this is what is stopping apt-get from reading these packages from the cache (please correct me if my guess is wrong).

If this really is the case please tell me which command should I use to change the group of all the packages to 'plugdev'. Doing the same from the nautilus properties window is time consuming as the number of packages is 505 (large).

If this is not my problem the please point out the mistake I'm commiting and kindly help me.

Many thanks.

---

### Post by drs305 on 2008-09-01
The command you are asking for will change all the files in /var/cache/apt/archives (and subfolders) to root ownership and plugdev group.

```

sudo chown -R root:plugdev /var/cache/apt/archives

```

---

### Post by OffAxis on 2008-09-01
next time try apt on cd

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

---

### Post by bhadotia on 2008-09-01
> **drs305 said:**
> The command you are asking for will change all the files in /var/cache/apt/archives (and subfolders) to root ownership and plugdev group.

```

sudo chown -R root:plugdev /var/cache/apt/archives

```
Thanks foe the reply. By the way I did some searching and found the 'chgrp' command.
> next time try apt on cd

[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)
Well I have aptoncd but after I create a dvd (which I already have) I cannot add to it the packages I installed after its creation. That is why I had to come up with this odd sounding plan.:)

---

