---
title: "can't install Opera in 11.10"
date: 2011-10-12
forum: New to Ubuntu
---

### Post by carloslosgrande on 2011-10-12
Hi, I'm having some difficulty installing Opera, ie I can't.

I have various saved deb files for installing apps I like. 

They all installed just fine in the usual manner, except Opera which gives me an error;     [COLOR="Red"]opera_11.51.1087.i386.deb could not be opened[/COLOR]

I assumed that the last copy I had of Opera was outdated, so I downloaded the latest copy, same problem.

Any ideas?

Thanks,
Carl.

---

### Post by -kg- on 2011-10-12
If you're using 11.10 and not 10.10, Oneiric hasn't been released yet (supposed to be released on the 13th) and as such isn't supported in the General Forums yet.  You might have more luck in the Oneiric Development forum until it's officially released.  :

[http://ubuntuforums.org/forumdisplay.php?f=403]("http://ubuntuforums.org/forumdisplay.php?f=403")

If you meant 10.10, then you need to change the title. ;)

---

### Post by SimonErich on 2011-10-13
Hello carloslosgrande

I just installed Ubuntu 11.10 (not 10.10 - 11.10 was released today) and had the same problem with Opera.

This seems to be an issue with the Softwarecenter, because installing it from terminal was not a problem at all.

So just open your terminal (CTRL + ALT + T) and use the following line to install it:

```
sudo dpkg -i /path/to/opera.deb
```
(where path/to/ is the path you downloaded it to - if you did it with firefox it is
"~/Downloads/".)


regards Simon

---

### Post by beew on 2011-10-13
Just installed it, I am typing from it now.

Use the ppa and follow the instructions here.

[https://help.ubuntu.com/community/OperaBrowser](https://help.ubuntu.com/community/OperaBrowser)

P.S. I think there are some problems with right click install for some .deb files. I couldn't isntall googleearth with right click whether using the USC or gdebi, but using dpkg -i in the terminal installed it fine.

[http://ubuntuforums.org/showthread.php?t=1858507](http://ubuntuforums.org/showthread.php?t=1858507)

---

### Post by carloslosgrande on 2011-10-13
Yes, that did it, thanks Simon and Beew

---

### Post by ruario on 2011-10-18
> **SimonErich said:**
> This seems to be an issue with the Softwarecenter, because installing it from terminal was not a problem at all.

You are right. It is a software center bug
[http://my.opera.com/community/forums/findpost.pl?id=10564932](http://my.opera.com/community/forums/findpost.pl?id=10564932)

---

