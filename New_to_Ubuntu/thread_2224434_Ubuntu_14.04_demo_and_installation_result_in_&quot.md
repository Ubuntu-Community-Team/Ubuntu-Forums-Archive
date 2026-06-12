---
title: "Ubuntu 14.04 demo and installation result in &quot;low graphics mode&quot; error"
date: 2014-05-16
forum: New to Ubuntu
---

### Post by Enlighter on 2014-05-16
Hello,

I'm quite new to Ubuntu and willing to try it out. I'm currently using a Dell Inspiron 15R 3537 with an AMD graphics card (HD 8670 M). It used to have Ubuntu pre-installed (I can't recall what kernel), but i formatted everything and installed Windows 7, and later on Windows 8.1. 

     After a while, when I tried to bring back Ubuntu into my laptop, the "low graphics mode" problem occurred. Particularly, it happened right after I finished installing 12.04 using Wubi (not LiveCD). However, after following a thread on AskUbuntu ([http://askubuntu.com/questions/141606/how-to-fix-the-system-is-running-in-low-graphics-mode-error](http://askubuntu.com/questions/141606/how-to-fix-the-system-is-running-in-low-graphics-mode-error)), I managed to fix the problem via the "apt-get update" command.

     But, here is the real problem. I created a bootable USB for Ubuntu 14.04 with Pen Drive Linux's USB Installer (that is, in Windows 8.1; I removed Wubi and 12.04 after another while). When i booted from the USB and chose "to try Ubuntu before installing", the same "The system is running in low graphics mode" occurred. I haven't installed from the LiveCD yet, instead i chose the "Check disc for defects" option, and it resulted in 5 errors being found, specifically they all came with the notification "no such file or directory" (i don't know what 5 files they are exactly). I checked the MD5 Checksum of the ISO image and it was OK, my laptop is not low on disk space and the AMD graphics drivers are working fine (on Windows that is).

     I know the "low graphics mode" issue itself can be solved, but my question is: How can i create an error-free bootable USB?

---

