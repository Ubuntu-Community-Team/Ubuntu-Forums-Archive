---
title: "No network connection"
date: 2008-09-01
forum: New to Ubuntu
---

### Post by speedzor on 2008-09-01
hi,

I've got a desktop in which I can't connect to the network.
Every time I enter my WEP-code, he's searching for the network (named: 'linksys'), but after some time, the popup is back to enter my code. 

At the moment of writing this, my laptop is 30cm next to the desktop, but connected to the network...

I'm using Ubuntu 8.04 with gnome.

how can I fix this?
greetings,
speedzor

---

### Post by david sousa on 2008-09-01
Maybe you could use ndiswrapper. If this is the case then com [here]("http://ubuntuforums.org/showthread.php?t=905350") ;)

---

### Post by james_vanb on 2008-09-01
First disable WEP and confirm that you can connect.  If you can, set WEP again - reboot.  While network manager is searching for connection, open terminal and:

```
sudo iwconfig wlan0 key XXXXXXXXXX
```

Where XXXXXXXXXX is your WEP key.  If that gets you connected, left click network manager, manually configure and reboot.  If it doesn't connect on subsequent boots, left click network manager, click manually configure, untick wireless (It sill automatically retick), untick again and retick - This will reset network configuration and connect.  Network manager appears to be a little buggy with WEP anymore.  Or you can leave it set to Roaming and run command when you boot.

---

### Post by speedzor on 2008-09-01
I've done this. Now I get the 4 bars, which indicate a connection, but it's at 0%, so no internet available.

---

### Post by james_vanb on 2008-09-01
Did you disable encryption at router and reboot?

---

### Post by speedzor on 2008-09-01
I did, no network.

---

### Post by james_vanb on 2008-09-01
What wireless card are you using?  How did you install the drivers?

Post output of:

```
lshw -C network
```

---

### Post by speedzor on 2008-09-01
```
jeroen@jeroen-desktop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 8
       bus info: pci@0000:00:08.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network:1
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 74
       serial: 00:0d:87:ba:4f:e7
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=via-rhine driverversion=1.4.3 latency=32 maxlatency=8 mingnt=3 module=via_rhine multicast=yes
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:0c:41:63:b0:71
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

```

---

### Post by james_vanb on 2008-09-01
Ah, the infamous Broadcom 4306.  My wireless card is a Belkin F5D7000 using the same chipset.  I had to use ndiswrapper and the Belkin install CD to get it working.  The driver I'm using is the bcmwl5.  If you have the install CD, you can identify the driver by inserting the CD, navigate to XP Drivers and look for the .inf file.  If yours is also the bcmwl5, I used this tutorial beginning at Step 2 to get it loaded and a connection.

[http://ubuntuforums.org/showthread.php?t=766560&highlight=bcmwl5](http://ubuntuforums.org/showthread.php?t=766560&highlight=bcmwl5)

Post the .inf from your CD.

---

### Post by speedzor on 2008-09-01
I can't find the cd, as the pc is already 4 years old, and probably lost.
Is there another way to find out what my driver is?

edit:
at that topic, I have to install/download some things.
How can I do that, as I don't have an internetconnection?

---

### Post by james_vanb on 2008-09-01
> **speedzor said:**
> I can't find the cd, as the pc is already 4 years old, and probably lost.
Is there another way to find out what my driver is?

 Try the manufacturers web site and/or google your wireless card.

> **speedzor said:**
> edit:
at that topic, I have to install/download some things.
How can I do that, as I don't have an internetconnection?

Easiest way is to run wire from desktop to router.  If that not possible, copy to usb stick, floppy, rewritable CD and then copy to your Ubuntu box.

---

### Post by david sousa on 2008-09-01
Did you follow my instructions? type lspci at the terminal. The last line which says network controller tells you your wireless card. then search for the correspondent driver

---

### Post by cwsnyder on 2008-09-01
You can probably go to another computer which is on the internet and download the driver from the manufacturer's website with the information on your LAN card, then use a thumb drive or CD-RW to copy the information to your system.

---

