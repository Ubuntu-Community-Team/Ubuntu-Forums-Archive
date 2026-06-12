---
title: "E:Unable to Locate Package"
date: 2013-04-27
forum: New to Ubuntu
---

### Post by MrSquiggles on 2013-04-27
I have noticed this thread before, but a solution was not found. I am getting the following error upon running a script:

Install-LoL-on-Wine.sh: 33: Install-LoL-on-Wine.sh: gnutls-cli: not found
"gnutls" not installed.

Which leads me to try:
sudo apt-get install gnutls

Resulting in:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package gnutls

I had several other packages missing, and I was able to install them using this method. gnutls however seems to pose a challenge. Any idea how to install it?

---

### Post by Elfy on 2013-04-27
Use the right package name :)

From a terminal 

```
apt-cache search gnutls
```

or try a search for gnutls - first result from googlubuntu

[https://help.ubuntu.com/community/GnuTLS](https://help.ubuntu.com/community/GnuTLS)

which would imply that 

```
sudo apt-get install gnutls-bin
```

will help.

You can also search for packages here

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by MrSquiggles on 2013-04-27
Thank You! Excellent response. You have solved my problem and taught me how to avoid it.

---

### Post by Elfy on 2013-04-27
welcome :)

you can have a look here to see how to mark thread as solved 

[http://ubuntuforums.org/showthread.php?t=2121377&p=12536730&viewfull=1#post12536730](http://ubuntuforums.org/showthread.php?t=2121377&p=12536730&viewfull=1#post12536730)

---

