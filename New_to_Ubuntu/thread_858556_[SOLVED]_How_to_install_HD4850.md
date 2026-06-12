---
title: "[SOLVED] How to install HD4850"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by cristo-father on 2008-07-13
Hi ubunters.
I am really desperate here, it is about my graphics card... i have tried restricted, envy, and manually installing catalyst, but none of these seem to work.
If anyone has any suggestion it will be immensely appreciated.

---

### Post by markbuntu on 2008-07-13
Follow this guide, Method 2. It has been reported to work with the HD 4850. If you are running 64 bit Hardy be sure and follow the special instructions for 64 bit.

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

If it works, you can use this guide to tweak it.

[http://forum.compiz-fusion.org/showthread.php?t=6794](http://forum.compiz-fusion.org/showthread.php?t=6794)

If it does not work, come back and tell us what went wrong.

If you already treid that, what exactly is going wrong?

---

### Post by cristo-father on 2008-07-14
> **markbuntu said:**
> Follow this guide, Method 2. It has been reported to work with the HD 4850. If you are running 64 bit Hardy be sure and follow the special instructions for 64 bit.

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

If it works, you can use this guide to tweak it.

[http://forum.compiz-fusion.org/showthread.php?t=6794](http://forum.compiz-fusion.org/showthread.php?t=6794)

If it does not work, come back and tell us what went wrong.

If you already treid that, what exactly is going wrong?
In the following topic you can see what is going wrong.

[http://ubuntuforums.org/showthread.php?t=858503&highlight=catalyst](http://ubuntuforums.org/showthread.php?t=858503&highlight=catalyst)

---

### Post by cristo-father on 2008-07-14
bump

---

### Post by cristo-father on 2008-07-14
bump

---

### Post by cristo-father on 2008-07-14
bump

---

### Post by cristo-father on 2008-07-14
bump

---

### Post by cristo-father on 2008-07-14
bump

---

### Post by cristo-father on 2008-07-14
bump

---

### Post by LowSky on 2008-07-14
Stop bumping threads 

> **LowSky said:**
> boot ubuntu in recovery mode from grub
It should come up with a screen asking if you wan to fix xorg or do something else.

if it doesn't and come up to a termial screen type this command

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

and why do you have 3 threads about the same issue?

---

### Post by cristo-father on 2008-07-26
> **LowSky said:**
> Stop bumping threads

I finally did it.

---

