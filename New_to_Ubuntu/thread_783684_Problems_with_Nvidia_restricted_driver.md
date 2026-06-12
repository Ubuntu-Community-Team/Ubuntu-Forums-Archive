---
title: "Problems with Nvidia restricted driver"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by Pyoro on 2008-05-05
First of all, sorry if this has already been posted, I tried searching and didn't find other mentions of this same problem.

I used Kubuntu 7.10 for a while and never had any problems with the Nvidia driver. About a week ago I installed 8.04 (clean install, not upgrade), and whenever I try to enable it (on Hardware Drivers Manager), after reboot all I get is a gray screen with some lines, something that looks like a black stain and a blue vertical bar that appears gradually.

The only way I can get it to work again is to revert to the old xorg.conf, which of course disables the driver again.

My video card is a Geforce 8400M GS. Is there a known way to solve this problem?

Thanks in advance :D

---

### Post by njparton on 2008-05-06
Have you tried installing via envy instead?
 
First use it to remove your current drivers and then to install them again.

---

### Post by skymera on 2008-05-06
+1 To ENVY.

It's availble in the repos is you have 8.04

```
 sudo aptitude update
sudo aptitude install envyng-gtk
```

---

### Post by Pyoro on 2008-05-06
Tried Envy, same result :(

One thing I forgot to mention: I'm using the amd64 version of Kubuntu.

---

### Post by Pyoro on 2008-05-08
**Update:** I tried to install the driver directly from Nvidia's website, and still, same result...

Here's a picture of what my screen looks like after installing the driver:

[[IMG]http://img81.imageshack.us/img81/6287/dsc02615cy1.th.jpg[/IMG]](http://img81.imageshack.us/my.php?image=dsc02615cy1.jpg)

---

