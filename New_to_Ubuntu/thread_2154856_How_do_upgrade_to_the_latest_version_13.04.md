---
title: "How do upgrade to the latest version 13.04"
date: 2013-06-16
forum: New to Ubuntu
---

### Post by Snitz on 2013-06-16
I just installed Ubuntu side-by-side with Windows 8.

I used windows installer to install Ubuntu and it gave me the 64bit and 12.04 version but now I can't upgrade it to the latest version.

What am I missing here?

---

### Post by fantab on 2013-06-16
You installed WUBI. WUBI installs Ubuntu inside Windows and not on a separate partitions or disk. 
However, WUBI is being phased out AFAIK because of its incompatibility with Windows8's 'SECURE BOOT'. The latest Ubuntu version 13.04 does not have WUBI.
WUBI installs are NOT true dual-boot. To have a true/real dual-boot you need to install Ubuntu on its own Partition.

Regarding your specific question: 

>  used windows installer to install Ubuntu and it gave me the 64bit and  12.04 version but now I can't upgrade it to the latest version.

How are you trying to upgrade and what error messages, if any, you are getting?

---

### Post by Snitz on 2013-06-16
I'm using the Update Manager, first time I did this it found 300MB of updates but now it's saying OS is up to date.

The problem is I don't have any USB stick or DVD to put Ubuntu on and install it so my only choice is to install it from Windows.

---

### Post by 3rdalbum on 2013-06-16
By default, LTS releases will not offer to upgrade to NON-LTS. Your 12.04 is a fully up-to-date 12.04.

To change the setting, go to Ubuntu Software Center. Go to the Edit menu and come down to Software Sources. Go to the Updates tab and you can change the setting there, to notify on normal releases.

Go to Update Manager and click Check. Shortly afterwards you will see a box at the top of the window that allows you to upgrade to 13.04.

---

### Post by Snitz on 2013-06-16
Thank you. I think it worked. It is now upgrading to 12.10

---

