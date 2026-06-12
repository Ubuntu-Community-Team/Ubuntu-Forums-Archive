---
title: "ndis wrapper and Dell Wireless 1505 Draft 802.11n"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by nutpants on 2008-05-03
i had it all working great last week but this week i have to reload the drivers each time

linux-laptop:~$  dmesg | grep ndiswrapper 
linux-laptop:~$ sudo ndiswrapper -l
[sudo] password for nutpants: 
bcmwl5 : driver installed
	device (14E4:4328) present
linux-laptop:~$ sudo depmod -a 
linux-laptop:~$ sudo modprobe ndiswrapper
nlinux-laptop:~$ dmesg | grep ndiswrapper   (
bash: syntax error near unexpected token `('
linux-laptop:~$ dmesg | grep ndiswrapper   
[  133.967426] ndiswrapper version 1.52 loaded (smp=yes, preempt=no)
[  134.042202] ndiswrapper: driver bcmwl5 (Broadcom,10/12/2006, 4.100.15.5) loaded
[  134.058760] ndiswrapper: using IRQ 17
[  134.142499] usbcore: registered new interface driver ndiswrapper
@linux-laptop:~/wifi$ sudo ndiswrapper -m
adding "alias wlan0 ndiswrapper" to /etc/modprobe.d/ndiswrapper ...

************************************************************************
*
* The update-modules command is deprecated and should not be used!
*
************************************************************************


i can see and scan (and see access points)with the wifi.. but the network manager can not see the wlan0: i have not found any commands to connect manually but i would prefer to connect with the network manager.

nutz

---

### Post by BaffledMollusc on 2008-05-03
I have a vague suspicion that to use the network manager applet you need to add "ndiswrapper" to the end of the file /etc/modules.

I have no idea why ndiswrapper isn't sticking between reboots, though. Maybe the kernel is trying to load another wifi driver module that conflicts with it and you need to blacklist it? Just guessing.

Edit: What did you do between last week and this week? Did you download any kernel updates?

---

