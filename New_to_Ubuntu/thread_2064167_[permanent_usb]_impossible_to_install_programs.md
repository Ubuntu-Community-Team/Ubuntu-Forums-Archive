---
title: "[permanent usb] impossible to install programs"
date: 2012-09-28
forum: New to Ubuntu
---

### Post by blacksmith11 on 2012-09-28
Hi all,
I hope I'm in the correct section because I never used linux and this forum too. 
I just made a permanent ubuntu usb by using universal USB installer from windows. Following the program steps I installed ubuntu on a 32 gb usb with a casper rw to save settings and what I have done. Everything seems to work correctly. Now I would like to install some programs and keep them always with me. However when I try to do it I get the following message:

ubuntu@ubuntu:~$ sudo apt-get install gnuplot-x11
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package gnuplot-x11

I don't get what's the problem. Can someone help?
Thanks everyone.

---

### Post by oldfred on 2012-09-28
Welcome to the forums.

The installer from Windows is just to create a USB instead of CD to install Ubuntu. Generally for small 4GB or less flash drives.

Installer CD is about 700MB so you can add a setting persistence to allow saving some files to those flash drives. But with a very large flash drive like yours you may want a full install.

Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)


Large persistent - C.S.Cameron post 6 & 7
[http://ubuntuforums.org/showthread.php?t=2041679](http://ubuntuforums.org/showthread.php?t=2041679)
With grub2 persistent C.S.Cameron 12.04
[http://ubuntuforums.org/showthread.php?t=2042965](http://ubuntuforums.org/showthread.php?t=2042965)

Full install of 12.04 to USB device C.S.Cameron post #5
[http://ubuntuforums.org/showthread.php?t=2060493](http://ubuntuforums.org/showthread.php?t=2060493)

Actually a full install to a extenal flash drive is just like any install to a second drive, but with a few settings to reduce writes. Both USB port and flash are slower than SATA or hard drive, but with reduced writes it is functional. I have a full install in 8GB with another 8GB on my 16GB for data.

It does not have to be encrypted BIOS based system:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory Installation using alternative text based installer
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
More discussion Dec 2010, more SSD info
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)

---

### Post by blacksmith11 on 2012-09-28
Thanks a lot Oldfred. Your explanation doesn't solve directly my problem but you gave me answers to many questions I had. However I installed a persistent usb ubuntu because in my net book I don't have cd-reader. I suppose I will do as you say and try a full installation!

---

