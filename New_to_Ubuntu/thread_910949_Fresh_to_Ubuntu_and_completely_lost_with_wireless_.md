---
title: "Fresh to Ubuntu and completely lost with wireless network"
date: 2008-09-05
forum: New to Ubuntu
---

### Post by Rooster628 on 2008-09-05
Hey folks,

I recently got my Ubuntu CD in the mail and went ahead and installed it onto my second hard drive, which wasn't doing much aside from keep my windows hard drive company. 

The installation went fine. No issues there. However, I don't seem to be able to connect to or even detect my wireless network at home. I have a total of 3 machines at home: 2 running XP and 1 running Vista (now dual booting with Ubuntu on a separate drive). Everything runs hunky dorey network-wise from every other machine or from Vista.

I've done some sniffing around and, unfortunately, haven't been able to troubleshoot this issue. So, I apologize if I may have over-looked anything that was already posted. 

As requested by the "Can't Connect to the Internet?" thread, here is my info:

- Attempting to connect via wireless router, D-Link DI-624 and using a Broadcom BCM4318 802.11g Wirelss LAN
- Provider is Comcast in the US
- Ubuntu 8.04
- Can't connect with any other method in Ubuntu since my only option from that location is wireless
- As evident here...I can connect to the internet at home from my other two machines or my main if I boot into Vista

lspci output:
```
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:03.0 Communication controller: Intel Corporation 82G33/G31/P35/P31 Express MEI Controller (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82566DC-2 Gigabit Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IH (ICH9DH) LPC Interface Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 6 port SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation Geforce 9600 GT 512mb (rev a1)
03:00.0 IDE interface: Marvell Technology Group Ltd. 88SE6101 single-port PATA133 interface (rev b2)
07:00.0 Communication controller: Conexant HSF 56k Data/Fax Modem
07:01.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
07:03.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
```

lsusb ouput:
```
Bus 008 Device 002: ID 090c:1000 Feiya Technology Corp. Memory Bar
Bus 008 Device 001: ID 0000:0000  
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 005: ID 413c:2003 Dell Computer Corp. 
Bus 002 Device 004: ID 046d:c043 Logitech, Inc. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
```

lshw -class network output:
```
  *-network
       description: Ethernet interface
       product: 82566DC-2 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: 00:1c:c0:21:de:0b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000e driverversion=0.2.0 firmware=1.3-0 latency=0 module=e1000e multicast=yes
  *-network
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:07:01.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:14:a5:d3:4c:98
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
```

Any help you folks could provide would be greatly appreciated :KS

---

### Post by Presto123 on 2008-09-05
I'm pretty sure that I have the exact same card in my laptop.

The best advice I can give you is to hook it up somewhere on a wired network and go into your "Restricted Drivers Manager" and enable the driver IF it shows up and select "Download from Internet" when it asks for a driver. I am a little confused if you are saying that it doesn't show up there or not...

Trust me, it will save you aggravation if you can get it to some kind of wired network to get the files. It SHOULD only take a few seconds to download the driver.

---

### Post by Rooster628 on 2008-09-05
> **Presto123 said:**
> I'm pretty sure that I have the exact same card in my laptop.

The best advice I can give you is to hook it up somewhere on a wired network and go into your "Restricted Drivers Manager" and enable the driver IF it shows up and select "Download from Internet" when it asks for a driver. I am a little confused if you are saying that it doesn't show up there or not...

Trust me, it will save you aggravation if you can get it to some kind of wired network to get the files. It SHOULD only take a few seconds to download the driver.

Getting a hard line connection is pretty much out of the question, sadly. The router is down the hall, down two flights of stairs and 2 rooms back. Although...I might be able to just download the drivers to a CD on one machine and load them from there.

---

### Post by NE Key on 2008-09-05
Have you had a look at the instructions here ?

(Howw to get a Broadcom wireless card working)

[http://ubuntuforums.org/showthread.php?t=870086&highlight=broadcom](http://ubuntuforums.org/showthread.php?t=870086&highlight=broadcom)

It worked for me.

---

### Post by Rooster628 on 2008-09-05
> **NE Key said:**
> Have you had a look at the instructions here ?

(Howw to get a Broadcom wireless card working)

[http://ubuntuforums.org/showthread.php?t=870086&highlight=broadcom](http://ubuntuforums.org/showthread.php?t=870086&highlight=broadcom)

It worked for me.

I just finished going through as much of that troubleshoot as possible and hit failures at every option :(

I appreciate the link though, it was worth the shot.

---

### Post by Kevbert on 2008-09-05
Please try this [[COLOR="Red"]post[/COLOR]]("http://ubuntuforums.org/showpost.php?p=5469730&postcount=13").

---

### Post by Rooster628 on 2008-09-05
> **Kevbert said:**
> Please try this [[COLOR="Red"]post[/COLOR]]("http://ubuntuforums.org/showpost.php?p=5469730&postcount=13").

You're my hero, Kevbert. I <3 you.

---

