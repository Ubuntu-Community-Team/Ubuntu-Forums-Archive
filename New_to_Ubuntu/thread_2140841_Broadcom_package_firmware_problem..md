---
title: "Broadcom package firmware problem."
date: 2013-04-30
forum: New to Ubuntu
---

### Post by deshoon on 2013-04-30
Hi there,

I'm not detecting a wireless signal. Wireless card is  BCM4311 802.11b/g WLAN, pci is [14e4:4311]. I have run the command " sudo apt-get install firmware-b43-installer" which returned the response "E: Unable to locate package firmware-b43-installer". Have previously run into system problems using the proprietory drivers method. Am using an acer extensa 5220 with a 1.8ghz celeron on board and am running 13.04. Any help would be appreciated,

Ta.

---

### Post by bkratz on 2013-04-30
> **deshoon said:**
> Hi there,

I'm not detecting a wireless signal. Wireless card is  BCM4311 802.11b/g WLAN, pci is [14e4:4311]. I have run the command " sudo apt-get install firmware-b43-installer" which returned the response "E: Unable to locate package firmware-b43-installer". Have previously run into system problems using the proprietory drivers method. Am using an acer extensa 5220 with a 1.8ghz celeron on board and am running 13.04. Any help would be appreciated,

Ta.



The first command is simply because you mentioned the proprietary drivers and might have installed the STA driver along the way. Ignore it if it says cannot find bcml------



sudo apt-get remove --purge bcmwl-kernel-source
 sudo apt-get install linux-firmware-nonfree


reboot and report your findings

---

### Post by deshoon on 2013-05-01
Hi bkratz,

Tried that and here are the results:

ubuntu@ubuntu:~$ sudo apt-get remove --purge bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'bcmwl-kernel-source' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ubuntu@ubuntu:~$ sudo apt-get install linux-firmware-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-firmware-nonfree

By the way, I'm running from a live usb drive, if that makes any difference.

---

### Post by bkratz on 2013-05-01
Did you have a working wired internet connection when you tried?  It will need one.  Also, if you are running from a live usb did you set up for persistence?  If not, it probably forgot when you did the reboot.

---

