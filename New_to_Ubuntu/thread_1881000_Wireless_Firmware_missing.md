---
title: "Wireless Firmware missing"
date: 2011-11-14
forum: New to Ubuntu
---

### Post by TovarishChump on 2011-11-14
I have recently installed ubuntu 11.10 onto my Dell Inspiron 1750. I cannot connect to the internet because the firmware is missing. I have looked up on various forums for what to do, however it is all Greek to me. I think I have found through terminal that I am using broadcom 43xx and the wireless is Disconnected? I do not have access to a wired connection. Can I download this firmware onto a flash drive from another computer and transfer across and install? I cannot re-install windows as I do not have the disk. Please help and bear in mind I am entirely ignorant with regards Linux and using terminal etc.
Thanks in advance.

---

### Post by TovarishChump on 2011-11-16
Here is some more information. It looks to me like the Wireless is disabled. PLEASE HELP!!!

---

### Post by TovarishChump on 2011-11-16
tovarishchump@tovarishchump-Inspiron-1750:/$ sudo lshw -C network
PCI (sysfs)  
  *-network               
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f69fc000-f69fffff
  *-network
       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 13
       serial: 00:25:64:56:c0:02
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 duplex=full firmware=N/A ip=192.168.0.9 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:44 memory:f68fc000-f68fffff ioport:de00(size=256)
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:22:5f:fe:2d:ce
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.0.0-12-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg
tovarishchump@tovarishchump-Inspiron-1750:/$

---

### Post by deltacomp on 2011-11-16
Hello please post the output of iwconfig ifconfig and lspci -nn

---

### Post by blueshead on 2011-11-16
Is there an on/off switch on your computer for wireless? My laptop won't connect unless I turn it on .. Also the light on the switch doesn't work in Ubuntu like it does in Win7..

---

### Post by deltacomp on 2011-11-16
I think this might help.

Open a terminal and type;

sudo apt-get install firmware-b43-installer

---

### Post by Immolatus on 2011-11-16
For this to work you'll need a wired network connection.
find the "restricted drivers" app that is present by default on all ubuntu installs since 7.xx (I think). Activate the "STA" driver. That one gave me the best results with my old Dell with the BCM43xx card.

---

### Post by deltacomp on 2011-11-16
Ooops that is correct, you will need an internet connection for my post. I will try to find firmware that can be saved to a USB drive and loaded.

---

### Post by Rex Bouwense on 2011-11-16
Don't you just love them Dells.  I have a Dell Inspiron 1000 and sought assistance here to install firmware.  See
[http://ubuntuforums.org/showthread.php?t=1869293](http://ubuntuforums.org/showthread.php?t=1869293).

---

### Post by TBABill on 2011-11-16
Just as an FYI, this card can be activated right from the live session before you install without ever needing a wired connection. I do it every time on 2 different brand machines with the BCM4312. All you do is fire up a live session, go to additional drivers, click the STA driver to activate it, then when it says you need to restart, DO NOT restart. Open a terminal and type ```
sudo modprobe wl
``` Wait about 30 seconds, select your network after clicking the network icon (upper right) and enter the encryption key, connect and enjoy. 
 
Once you connect in the live session, do your install and you will not ever have had to connect. Your reboot after installing the OS will bring you to the desktop with fully active connection already working.

---

