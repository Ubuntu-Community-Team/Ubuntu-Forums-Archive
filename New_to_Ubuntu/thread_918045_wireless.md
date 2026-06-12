---
title: "wireless"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by dsmcginn on 2008-09-12
ok, so this is like the third time posting in here asking questions, but everytime i get somewhere, somehow screw it up. lol. i'm trying to connect to my wireless router in my house. it's unsecured, but for some reason it won't show up under my network manager.

any help?

---

### Post by wolfen69 on 2008-09-12
first, let's find out what type of wireless you have. open a terminal and do: ```
lspci
```

---

### Post by dsmcginn on 2008-09-12
ps...i'm pretty much clueless with ubuntu, so you might have to break it down barney style for me. 

=)

---

### Post by dsmcginn on 2008-09-12
doug@doug:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
0a:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
doug@doug:~$

---

### Post by SunnyRabbiera on 2008-09-12
what kind of card are you using for wireless?
Fair warning: wireless in ubuntu is still not quite all there yet, this is more of a manufacturer issue then a Ubuntu one as most of them dont like linux/ubuntu.
One suggestion i can suggest is use Linux Mint as opposed to ubuntu as it has some tools built in for wireless like mintwifi:
[http://www.linuxmint.com/](http://www.linuxmint.com/)

Mint is based on Ubuntu but has some tools to make transition easier.

---

### Post by k33bz on 2008-09-12
What kind of computer are you using? Laptop? If so what brand and model?

---

### Post by wolfen69 on 2008-09-12
did you check system>administration>hardware drivers to see if the drivers are there?

---

### Post by bobnutfield on 2008-09-12
This chipset is apparently supported by madwifi, and I believe madwifi is in the repositories.  There is also information here:

[http://madwifi.org/]("http://madwifi.org/")

A quick google found quite a bit about this chipset in other formums.

---

