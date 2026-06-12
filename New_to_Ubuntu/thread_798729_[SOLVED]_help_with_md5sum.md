---
title: "[SOLVED] help with md5sum"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by paydaydaddy on 2008-05-18
Okay, I am an obvious bonehead. I have done this several times before, but I can't figure it out now. I downloaded ubuntu 8.04 and want to check the md5sum before burning to cd. I have the file on my desktop but I must be leaving out something when I try to access the file to check the md5sum. ```
cd /home/dragon/Desktop
```gets me to the desktop, but then what command do I use to access the iso file: ubuntu-8.04-desktop-i386? Everything I have tried so far has returned an error. I am working on a computer with kubuntu 8.04 installed.

---

### Post by solar george on 2008-05-18
```
cd Desktop/
md5sum ./ubuntu-8.04-desktop-i386
```

Hint: the tab key autocompletes files/commands

---

### Post by paydaydaddy on 2008-05-18
Thanks solar george. That was the info I needed.

---

### Post by seetho on 2008-05-18
You should also download the file containing the md5sum hash value.  Normally this is "MD5".  It contains a list of hash value and the corresponding file names.  To verify all the files just do the following:

md5sum -c MD5

---

