---
title: "can i update my nautilus in 8.04 to the latest stable release???"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by stinger30au on 2008-10-18
i had a quick look here 

[http://www.gnome.org/projects/nautilus/](http://www.gnome.org/projects/nautilus/)

and found the latest stable version is here

[http://ftp.acc.umu.se/pub/GNOME/sources/nautilus/2.24/](http://ftp.acc.umu.se/pub/GNOME/sources/nautilus/2.24/)

can i install this to 8.04 , and if so how?

---

### Post by t0p on 2008-10-18
That ftp link is to the source code for nautilus 2.24.0.  If you want to use it, you'll have to compile it yourself.

Nautilus is bundled with distros, and that's the way it's "meant" to be used.  Compiling it yourself will be an adventure, if you've never done it before.

---

### Post by stephanvaningen on 2008-10-18
I found that checkinstall can create .deb files
So:
```
sudo apt-get install checkinstall
```
installs the tool to start with, next is look at last thread (@ February 4th, 2006, 03:02 PM) in this topic: [http://ubuntuforums.org/archive/index.php/t-125409.html]("http://ubuntuforums.org/archive/index.php/t-125409.html")

Is that the direction you want to go to? You can also just leave it: the Ubuntu will move to a next version of Nautilus when necessary

---

### Post by stinger30au on 2008-10-18
thanks for the info guys. done some reading and learning. i have never complied anything in my life and looks like something way over my head


i think i will wait till 8.10 gets released and backup and reinstall fresh

---

