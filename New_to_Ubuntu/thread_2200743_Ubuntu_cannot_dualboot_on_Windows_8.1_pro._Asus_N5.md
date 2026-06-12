---
title: "Ubuntu cannot dualboot on Windows 8.1 pro. Asus N56VB laptop"
date: 2014-01-20
forum: New to Ubuntu
---

### Post by Jeremy_Lai_Wai_Kit on 2014-01-20
Installed Ubuntu in Windows 8.1 
Disabled UEFI fastboot
Disabled Windows Secureboot. 

I've done all from above, but it doesn't seem to work. On startup, my computer took me to the WIndows 8 boot screen where it allows me to select an OS. I clicked ubuntu and a black screen named WIndows Boot Manager saying "Windows failed to start. A recent hardware or software change might be the cause, try to fix the problem"

"File : \ubuntu\winboot\wubildr.mbr
Status: 0xc000007b
info: The application or operating system couldn't be loaded because a required file is missing or contains errors."

What's going on?

---

### Post by Evan_Hart on 2014-01-20
did you use boot repair? you have to run it in live from your installation media

---

### Post by oldfred on 2014-01-21
Wubi does not work with gpt partitioned drives or any system that is pre-installed with UEFI boot.

Because all new computers are UEFI with gpt, 12.04 is the last supported version of wubi.

With UEFI better to install to separate partitions anyway. See links in link in my signature if planning to do that.

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

---

