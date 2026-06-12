---
title: "upgrade/get newer version of GEdit on ubuntu 12.04?"
date: 2014-06-06
forum: New to Ubuntu
---

### Post by asiancraig2 on 2014-06-06
i'm on ubuntu 12.04 and my gedit is 3.41, it's the only version available to me.  How do upgrade or get a newer version of gedit on ubuntu 12.04?

---

### Post by palmerito0 on 2014-06-06
You can update all programs on Ubuntu with ```
sudo apt-get update
```

Try ```
sudo apt-get install gedit
```. Ubuntu will then check for possible updates


Good Luck ):P:lolflag:

---

### Post by asiancraig2 on 2014-06-07
> **palmerito0 said:**
> You can update all programs on Ubuntu with ```
sudo apt-get update
```

Try ```
sudo apt-get install gedit
```. Ubuntu will then check for possible updates


Good Luck ):P:lolflag:

nope still gives gedit 3.4.1. as the latest, no updates... i see there is up to 3.11 gedit on their site, how do i install..

---

### Post by claracc on 2014-06-07
As far as I know, there is not a deb gedit's package for ubuntu 12.04 above 3.4.1. See [https://launchpad.net/ubuntu/+source/gedit](https://launchpad.net/ubuntu/+source/gedit). 

As you want gedit 3.11 : [http://ftp.gnome.org/pub/GNOME/sources/gedit/3.11/](http://ftp.gnome.org/pub/GNOME/sources/gedit/3.11/) you will have to download the tar source file and compile it for your system. But I think you are going to encounter certain problems since it seems a not easy task,  dependencies problems will surely arise.

This link: [http://askubuntu.com/questions/411831/updating-gedit-by-compile-make-and-install-the-tar-xz](http://askubuntu.com/questions/411831/updating-gedit-by-compile-make-and-install-the-tar-xz) can help you, in the answers are addresses to fix problems in compiling.

---

