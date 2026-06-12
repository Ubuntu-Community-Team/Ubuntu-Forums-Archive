---
title: "E:  Couldn't find package Ntfstools"
date: 2008-07-02
forum: New to Ubuntu
---

### Post by pensaer on 2008-07-02
Hey everybody,
I'm an absolute ubuntu noob looking to start the frustrating process of dual booting hardy with xp on a raid 0 array.  problem is, i can't even get the fun part, i'm stuck trying to change my windows partition size... every time i run apt-get install ntfstools i get the following:

ubuntu@ubuntu:~$ sudo apt-get install ntfstools
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ntfstools

thanks in advance

---

### Post by Fixman on 2008-07-02
If you want to change the size of a windows partition I recommend you to download parted, and its GUI gparted. To do this just write on the terminal

```
 sudo apt-get install gparted 
```

Then go to system->administration->partition editor

---

### Post by pensaer on 2008-07-02
Gparted doesn't recognize my raid array... or at least doesn't let me change anything after showing both disks as one unpartitioned disk

---

### Post by drs305 on 2008-07-02
I think what you are calling *ntfstools* may be **ntfsprogs**, which is in synaptic.  

ntfsprogs: various tools for managing ntfs, namely mkntfs, ntfsresize, ntfsclone, ntfsfix, ntfsundelete, ntfswipe and ntfsdecrypt.

---

