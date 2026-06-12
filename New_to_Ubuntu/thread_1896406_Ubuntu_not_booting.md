---
title: "Ubuntu not booting"
date: 2011-12-16
forum: New to Ubuntu
---

### Post by e61016 on 2011-12-16
Have installed Ubuntu 11.10 with dual boot using Wubi on Dell Inspiron 1525.
Has been working fine for months until now.
Problem: the screen and cursor froze. Powered down. When tried to boot, it gave me a pink screen and froze.  When tried to boot in recovery mode, it stated "Loading ramdisk" and then froze.

Windows Vista portion works fine.  Do I need to re-install from Wubi?  If so, would I loose data in Ubuntu?

Any help is appreciated.

---

### Post by fantab on 2011-12-16
> **e61016 said:**
> Have installed Ubuntu 11.10 with dual boot using Wubi on Dell Inspiron 1525.
**Has been working fine for months until now**.
Problem: the screen and cursor froze. Powered down. When tried to boot, it gave me a pink screen and froze.  When tried to boot in recovery mode, it stated "Loading ramdisk" and then froze.

Windows Vista portion works fine.  Do I need to re-install from Wubi?  If so, would I loose data in Ubuntu?

Any help is appreciated.

Welcome!

WUBI is not a permanent way to use UBUNTU and it is not encouraged to be used "for months. If you have done** trying** INSTALL Ubuntu to its own Partition. Its time.

Back up all your important DATA and Un-install Ubuntu from Windows Add/remove Programs or any other Uninstaller. 

From Windows make some space for Ubuntu about at least 30GB. Using Ubuntu LiveCD create a ext4 partition of the space you've created and format it as " / " and install Ubuntu. 

If you have Data on Ubuntu and you cannot access it with Windows then use LiveCD to access that Data and back it up.

**[See Here]("http://members.iinet.net.au/%7Eherman546/index.html")** to learn how to dual boot Ubuntu with Windows.

---

### Post by bcbc on 2011-12-17
Yes if you reinstall you'll lose all the data from your Wubi install. 

You should try:
1. running chkdsk from Windows
2. If it still doesn't work, run fsck on the root.disk (you'll need an Ubuntu CD to do this).

In the meantime, you can try to recover your data with this tool from windows: [http://ext2read.blogspot.com/](http://ext2read.blogspot.com/) (it can be flaky, but it works - just point it at the \ubuntu\disks\root.disk)

---

### Post by wildmanne39 on 2011-12-17
Hi ranaponting, you should start your own thread with a good title so you can get the answers to your question.
Thank you

---

