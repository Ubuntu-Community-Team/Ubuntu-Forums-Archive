---
title: "Play .dat file"
date: 2011-10-24
forum: New to Ubuntu
---

### Post by jaganpks on 2011-10-24
Hi,

I'm trying to play .dat files (VCD files). But I'm unable to do so. I tried with VLC as well as Movie Player. 

I followed the steps in another thread "[http://ubuntuforums.org/showthread.php?t=1835861&highlight=play+.dat+files](http://ubuntuforums.org/showthread.php?t=1835861&highlight=play+.dat+files)", but it didn't work for me.

Please help me with this.

---

### Post by cavh on 2011-10-24
It's polite to end requests with the word 'please'.

---

### Post by jaganpks on 2011-10-24
Sorry, I forgot that.

If you know the ans. please post

---

### Post by TeoBigusGeekus on 2011-10-24
Put the cd in the tray and try this
```
vlc vcd:///dev/sr0
```
Replace sr0 with whatever applicable (dvd, cd, cdrw, etc.)

---

### Post by blackmail on 2011-10-24
Please try to install gxine, it also has a frontend, and it was the best tool for such things when i used it, mainly it will resurface again between my apps just have to get home and install the stuff...

all in all try gxine
sudo apt-get install gxine
or give a search for it with aptitude, or use the SW Center

---

