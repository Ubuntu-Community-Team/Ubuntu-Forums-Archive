---
title: "[SOLVED] I erased &amp;quot;libhal.so.1&amp;quot;"
date: 2008-10-22
forum: New to Ubuntu
---

### Post by kattman on 2008-10-22
I erased "libhal.so.1"
Is there anyway I can find a copy!  
Its should be in  "usr/lib"   
Will someone copy thiers to "http://filebin.ca/"

thanks
kattman

---

### Post by scragar on 2008-10-22
Just reinstall libhal1 via either:```
apt-get install --reinstall libhal1
```or by downloading the deb and doing it that way(if you've got a slow net or something it'd work)
[http://packages.ubuntu.com/hardy/libhal1](http://packages.ubuntu.com/hardy/libhal1)

PS: 32bit or 64 bit?

---

### Post by kattman on 2008-10-22
Ububtu will not boot! apt-get wont work nor can I install a .deb


kattman

---

### Post by scragar on 2008-10-22
OK, since we don't appear to be getting the most important question answered(32 bit or 64 bit -- we never even got to what version your running) I come bearing 2 gifts.

---

### Post by kattman on 2008-10-22
Thanks Guys, I found it!!

---

### Post by patrickballeux on 2008-10-22
You could have booted with the live-cd, and copy the file from the live cd to your hardisk...  (Hoping that the CD is the same version as the installed distribution).

If not, download the files with the live cd, and copy the right one on your harddrive.

It makes me remember the time I forced the installation of a libc6(something) package just to be able to install a game... nasty thing happened...  no more reboot possible!  I fixed by downloading the right package, and copying the content on the harddisk to overwrite the wrong files...  I'll never do that again!

Good luck!

---

