---
title: "install gd lib 2.0.28 or greater"
date: 2007-09-24
forum: Programming Talk
---

### Post by thushw on 2007-09-24
can i use apt-get to install gd lib 2.0.28 or later? currently phpinfo() tells me i have gd 2.0 or higher. i'm trying to figure out why imagecreatefromgif() fails for just **some** gifs...

the only info i found on this says i need to have gd lib 2.0.28 or higher. the gd.so that gets installed with apt-get install php5-gd doesn't have a version number in the file name. i do have these files (that look like 2.0.34 version of the gd lib?):


root@thushw-laptop:/usr/lib/php5/20060613+lfs# ls -l /usr/lib/libgd.so.2
lrwxrwxrwx 1 root root 15 2007-09-24 00:25 /usr/lib/libgd.so.2 -> libgd.so.2.0.34

any help much appreciated.

thushara

uname -a:  Linux thushw-laptop 2.6.20.3-ubuntu1 #2 SMP Sun Apr 15 11:26:58 PDT 2007 i686 GNU/Linux
apache: Apache/2.2.3
php 5

---

### Post by thushw on 2007-09-24
for now, what i have done is to manually copy over a version of libgd.so that works (from a centos installation) and make the /usr/lib/libgd.so.2 point to it...

---

