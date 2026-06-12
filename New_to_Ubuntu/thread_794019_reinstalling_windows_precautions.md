---
title: "reinstalling windows: precautions"
date: 2008-05-14
forum: New to Ubuntu
---

### Post by dhawald3 on 2008-05-14
Hi

I was having dual boot ubuntu and windows with grub boot loader.

Now My windows installation has developed some problem and I am going to reinstall it on my pc.

After installation will the grub boot loader be still there or the windows installation will replace it?

if not what is the procedure to keep my ubuntu installation alive???

---

### Post by Joeb454 on 2008-05-14
Windows will overwrite Grub, so you'll need to reinstall it from a LiveCD :( It's because Windows (naturally) doesn't like Linux.

I'll find the wiki link :)

Found the link now :)

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by tacutu on 2008-05-14
the windows boot loader will override grub.
after installing windows, boot from the live cd and reinstall grub. Try 
```
grub-install
```
from the command line once into the live environment.

---

### Post by bodhi.zazen on 2008-05-14
There are two issues :

1. Be careful with windows. It needs to be installed into a primary partition and take care it does not install into the entire hard drive.

2. You will need to restore GRUB. This is easy, use the Ubuntu live CD, and follow the link Joeb454 gave.

---

