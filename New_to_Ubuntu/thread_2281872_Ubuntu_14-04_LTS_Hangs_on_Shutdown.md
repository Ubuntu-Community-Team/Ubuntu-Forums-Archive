---
title: "Ubuntu 14-04 LTS Hangs on Shutdown"
date: 2015-06-10
forum: New to Ubuntu
---

### Post by Steve_Brook on 2015-06-10
Hi, I am new to 14-04 though I have used Ubuntu in the past.   Enjoying it so far after just having changed from fedora 19.

However i started to have a problem with it refusing to shut down, it would just hang there with the Ubuntu dots changing colour.  I had a feeling it may be to do with Wireless networking as I had tried and failed to get it working (wasn't too bothered as I also have a Gbit wired connection)

Searching through these forums I found the thread [http://ubuntuforums.org/showthread.php?t=2217602](http://ubuntuforums.org/showthread.php?t=2217602) on which a lot of people were suggesting manual ways to force the shutdown.  OK but not what I wanted, I wanted it to work properly.  Further down the thread I found that drphysic had had a problem with his Broadcom WiFi card causing the hang and had solved it by purging the bcmwl-kernel-source.  I tried it and it seemed to work.

I wanted to get the Wless working though, so I did some searching and found this page [https://wireless.wiki.kernel.org/en/users/Drivers/b43#devicefirmware](https://wireless.wiki.kernel.org/en/users/Drivers/b43#devicefirmware) where you can check your hardware and if it is supported.  Luckily mine was, so I followed the link to [http://linuxwireless.sipsolutions.net/en/users/Drivers/b43/](http://linuxwireless.sipsolutions.net/en/users/Drivers/b43/) which tells you how to install the correct firmware drivers



[LIST]
[*]                           :razz:Glad to say, Ubuntu has a very easy fix - simply run this in a Terminal, reboot and everything shuts down OK, and on reboot it finds and gets working my Wless card  -  simples
sudo apt-get install firmware-b43-installer 
[/LIST]

---

### Post by seijirou on 2015-06-10
So are you saying that you are still having a problem?

---

