---
title: "fakeroot?"
date: 2011-10-04
forum: New to Ubuntu
---

### Post by joshcanfield on 2011-10-04
hey i have just installed ubuntu on a windows laptop that crashed on me. so far most everything works except i keep getting this.......

Errors were encountered while processing:
 bcmwl-kernel-source
 fakeroot

the lap top is a dell inspiron mini 10... it used to have windows xp service pack three but crashed so i installed ubuntu 10.04 notebook edition on it. 

if any body can give me a push in the right direction about what this means that would be great thanks.

oh also me screen is real glitchy when scrolling down a page or opening a menu it looks as though the image is flashing and i see horizontal lines between screen changes. is there a way to change this?

thanks 
josh

---

### Post by IWantFroyo on 2011-10-04
```
sudo apt-get install -f
```
That should fix any issues you have in packaging.

As for the graphics problems, have you installed any drivers onto your system?

---

### Post by joshcanfield on 2011-10-04
tried the command and got this

```
joshua@joshua-laptop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up bcmwl-kernel-source (5.60.48.36+bdcom-0ubuntu3) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing bcmwl-kernel-source (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up fakeroot (1.14.4-1ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing fakeroot (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 bcmwl-kernel-source
 fakeroot
E: Sub-process /usr/bin/dpkg returned an error code (1)
joshua@joshua-laptop:~$ 
```

no i have not installed any new drivers yet besides the one for my wireless card

edit: i checked and it shows that there are no drivers that need to be installed

i installed gimp and it gave the fakeroot error but gimp seems to work just fine. I dont know if any of this helps at all but its what all i have came across. since i last posted.

---

