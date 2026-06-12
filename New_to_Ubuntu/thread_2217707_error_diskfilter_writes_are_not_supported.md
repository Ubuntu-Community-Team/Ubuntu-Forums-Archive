---
title: "error: diskfilter writes are not supported"
date: 2014-04-18
forum: New to Ubuntu
---

### Post by ram13 on 2014-04-18
I just installed ubuntu server 14.10 on a usb flash drive. Previously I had 13.10 server which doesn't show any error but 14.10 shows "error: diskfilter writes are not supported" on boot then it continuous to boot without problem. One more change that I made is; previously I had /boot, now I have just efi and lvm partitions

any suggestion to get rid this issue? thanks

---

### Post by Gone fishing on 2014-05-01
Having the same problem it's a bug [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1274320](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1274320) note post 34  has a fix I might try it

---

### Post by Gone fishing on 2014-05-01
Yes the fix works

---

### Post by agarrett5 on 2014-07-14
Having same message, but it doesn't continue to boot.  I have tried the work around and it didn't work.  Any suggestions?  I tried upgrading from 12.04 to 14.04.  I have no gone back to a working 12.04 system with Zimbra on top.  Am reluctant to move to 14.04 unless I have a very likely workable work around

---

### Post by Menion on 2014-08-23
Hi
I'm running Ubuntu 14.04 or better XBMCbuntu Gotham 13, that as base is an Ubuntu 14.04
I'm getting this error, but no one of the suggested patch works for me
I've tried also to set quick_boot="0" set GRUB_SAVEDEFAULT=false as suggested here: [https://forum.manjaro.org/index.php?topic=7425.0](https://forum.manjaro.org/index.php?topic=7425.0) but still having the error (boot process is just fine)

---

### Post by grahjenk on 2015-04-30
The Really Sad thing is that the problem still hasn't been fixed in Ubuntu 15.04!

---

