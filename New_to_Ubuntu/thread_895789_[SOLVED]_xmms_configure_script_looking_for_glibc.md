---
title: "[SOLVED] xmms configure script looking for glibc"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by mdecler2 on 2008-08-20
XMMS configure script is looking for standard GNU libraries and not finding any. Isn't this supposed to come standard with Ubuntu?

Do I need to install glibc from source? [ftp://ftp.gtk.org/pub/glib](ftp://ftp.gtk.org/pub/glib)

---

### Post by Titan8990 on 2008-08-20
just do:

apt-get install xmms


This will install any dependencies you need along with XMMS.

---

### Post by Eisenwinter on 2008-08-20
> **Titan8990 said:**
> just do:

apt-get install xmms


This will install any dependencies you need along with XMMS.
Xmms has no deb package on Hardy, verify he's NOT using Hardy at first.
-

mdecler2: if you're using Ubuntu Hardy (8.04), you can try out xmms packages for Gutsy (7.10), and see if it works.

I haven't gotten xmms to compile from source on Hardy either, due to the same problem glib. Though I do have glib installed, I didn't understand why it didn't compile.

I eventually managed to get it compiled and installed, but with some problems, I actually don't remember what I did, though. If I try to install a deb package of xmms, it gives me dependency problems.

---

### Post by ajgreeny on 2008-08-20
Unfortunately, if you're running Hardy 8.04, xmms is not available from the repos. so ```
sudo apt-get install xmms
``` will get you nowhere.  I don't know if you can install it from the Gutsy 7.10 repos, but others may know about this.  There are other music players, however, that are available, so unless you particularly need xmms for some reason, try something else.

OK, too slow, but same advice goes!

---

### Post by Titan8990 on 2008-08-20
Sorry, should have asked for the version. I am still running gutsy. I just searched the repositories and saw that it was there.

---

### Post by mdecler2 on 2008-08-20
I installed glib version 1.2.2 successfully from source, but gtk+ version 1.2.2 is failing because it can't find X libraries.

Maybe someone could give me an alternative to xmms? Preferably much smaller footprint than amarok!

I am a fan of foobar2000 in Windows just because of the light weighted-ness and simplicity.

---

### Post by Titan8990 on 2008-08-20
I personally like VLC. It is very lightweight and comes stock with every codec you can think of:

sudo apt-get intall vlc

---

### Post by mdecler2 on 2008-08-29
I solved my issues with installing xmms, and felt like cleaning up this thread. Please go to another thread I started:
[http://ubuntuforums.org/showthread.php?t=901932](http://ubuntuforums.org/showthread.php?t=901932)

You will find links to what dependencies you should install from the repos, including the correct glibc libraries, from the other thread.

---

### Post by nicedude on 2008-08-29
To install xmms cleanly and easily you can find a deb package for hardy that installs cleanly buy just googling for it.

---

### Post by markbuntu on 2008-08-29
xmms debs:
 i386

[https://launchpad.net/ubuntu/hardy/i386/xmms/1:1.2.10+20070601-1build2](https://launchpad.net/ubuntu/hardy/i386/xmms/1:1.2.10+20070601-1build2)

amd64:

[https://launchpad.net/ubuntu/hardy/amd64/xmms/1:1.2.10+20070601-1build2](https://launchpad.net/ubuntu/hardy/amd64/xmms/1:1.2.10+20070601-1build2) 

Beware of dependency problems with libglib1.2 and libglib1.2dbl on the amd64 build, i386 is no problem. You can read about that here:

[http://ubuntuforums.org/showthread.php?t=774461](http://ubuntuforums.org/showthread.php?t=774461)

---

