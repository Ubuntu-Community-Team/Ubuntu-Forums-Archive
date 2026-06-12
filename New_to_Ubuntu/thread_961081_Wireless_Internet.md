---
title: "Wireless Internet"
date: 2008-10-28
forum: New to Ubuntu
---

### Post by Torak on 2008-10-28
I'm currently using Ubuntu 8.04 LTS dual booting Windows Vista. My Vista internet is working fine but my Ubuntu internet is not. I have tried many times to start a tutorial but some things seem missing. Such as the Device Manager witch should apparently already be there according to this [https://help.ubuntu.com/8.04/internet/C/troubleshooting.html](https://help.ubuntu.com/8.04/internet/C/troubleshooting.html) . And I cant seem to be able to install the ndisgtk. So if anyone can help me at all it would be appreciated.

---

### Post by Gone fishing on 2008-10-28
I think the first thing you should do is open a terminal and type:

sudo iwconfig

This will list if there is a wireless device that Ubuntu can use attached to the PC. If there isn't then possibly you will need to use the ndswrapper to install drivers from Windows, if there is, then it can be configured using the network config tool System > Administration > Network

---

### Post by Torak on 2008-10-28
> **Gone fishing said:**
> I think the first thing you should do is open a terminal and type:

sudo iwconfig

This will list if there is a wireless device that Ubuntu can use attached to the PC. If there isn't then possibly you will need to use the ndswrapper to install drivers from Windows, if there is, then it can be configured using the network config tool System > Administration > Network

I have done sudo iwconfig and it does show my driver is there but there is no wireless option under System > Administration > Network.

---

### Post by marshalium on 2008-10-28
> **Torak said:**
> I have done sudo iwconfig and it does show my driver is there but there is no wireless option under System > Administration > Network.

It would help if you posted the output of iwconfig and lspci here.

---

### Post by Torak on 2008-10-28
> lspci

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT 
Express Memory Controller Hub (rev 03)
00:02.0
VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML 
Express Integrated Graphics Controller (rev 03)
00:02.1 
Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML 
Express Integrated Graphics Controller (rev 03)
00:1b.0 
Audio device: Intel Corporation 82801G (ICH7 Family) 
High Definition Audio Controller (rev 02)
00:1c.0 
PCI bridge: Intel Corporation 82801G (ICH7 Family) 
PCI Express Port 1 (rev 02)
00:1d.0 
USB Controller: Intel Corporation 82801G (ICH7 Family) 
USB UHCI Controller #1 (rev 02)
00:1d.1 
USB Controller: Intel Corporation 82801G (ICH7 Family) 
USB UHCI Controller #2 (rev 02)
00:1d.2 
USB Controller: Intel Corporation 82801G (ICH7 Family) 
USB UHCI Controller #3 (rev 02)
00:1d.3 
USB Controller: Intel Corporation 82801G (ICH7 Family) 
USB UHCI Controller #4 (rev 02)
00:1d.7 
USB Controller: Intel Corporation 82801G (ICH7 Family) 
USB2 EHCI Controller (rev 02)
00:1e.0 
PCI bridge: Intel Corporation 82801 
Mobile PCI Bridge (rev e2)
00:1f.0 
ISA bridge: Intel Corporation 82801GBM (ICH7-M) 
LPC Interface Bridge (rev 02)
00:1f.1 
IDE interface: Intel Corporation 82801G (ICH7 Family) 
IDE Controller (rev 02)
00:1f.2 
SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) 
SATA AHCI Controller (rev 02)
00:1f.3 
SMBus: Intel Corporation 82801G (ICH7 Family) 
SMBus Controller (rev 02)
02:00.0 
Ethernet controller: Marvell Technology Group Ltd. 88E8038 
PCI-E Fast Ethernet Controller (rev 14)
03:09.0 
CardBus bridge: Texas Instruments PCIxx12 
Cardbus Controller
03:09.1 
FireWire (IEEE 1394): Texas Instruments PCIxx12 
OHCI Compliant IEEE 1394 Host Controller
03:09.2 
Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)


iwconfig

lo        no wireless extensions.



eth0      no wireless extensions.

Those are the results I get.

---

### Post by marshalium on 2008-10-28
iwconfig says that you have a "no wireless extensions" which means that your wireless card is not properly detected/installed by ubuntu.

Also I don't see your wireless card listed in lspci. 

Do you know what type/brand/model of wireless card you have?

If you're not sure a google search for your model of laptop will usually give the answer.

---

### Post by Torak on 2008-10-28
> D20125-003-001.exe - RealTek Network Driver Version: 6.1090.0608.2007
Taken from Gateway drivers download site.

---

### Post by marshalium on 2008-10-28
> **Torak said:**
> Taken from Gateway drivers download site.

Okay, its a RealTek card. Can you run lsusb? That should give the model number.

---

### Post by Torak on 2008-10-28
> **marshalium said:**
> Okay, its a RealTek card. Can you run lsusb? That should give the model number.

Whats lsusb? Something to type in the terminal? sudo lsusb? It's dual-boot so I have to switch every time I need to check something.

---

### Post by marshalium on 2008-10-28
> **Torak said:**
> Whats lsusb? Something to type in the terminal? sudo lsusb? It's dual-boot so I have to switch every time I need to check something.

'lsusb' is a command you run in the terminal. 

You don't need sudo. Just run it like you did lspci and iwlist.

If you can find the model number of your card somehow in windows that would work too. Whatever way you do it you will need to find the model of your wireless card before you can get it working.

---

### Post by macogw on 2008-10-29
To find it in Windows, hit the Windows key and the Break key at the same time, and the hardware info window should come up.

---

### Post by Torak on 2008-11-01
This is my driver from doing what macogw told me to do.

Realtek RTL8187B Wireless 802.11g 54Mbps USB 2.0 Network Adapter

---

### Post by marshalium on 2008-11-01
> **Torak said:**
> This is my driver from doing what macogw told me to do.

Realtek RTL8187B Wireless 802.11g 54Mbps USB 2.0 Network Adapter


[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/254438/comments/9](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/254438/comments/9)

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=6056428](http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=6056428)

According to these links it looks like your card is supported out-of-the-box in Ubuntu 8.10. 

I suggest you give 8.10 a try.

---

### Post by Torak on 2008-11-02
Ok! Great, should I try to uninstall Ubuntu 8.04 or use another live cd of 8.10 to upgrade witch would work better?

---

### Post by marshalium on 2008-11-02
> **Torak said:**
> Ok! Great, should I try to uninstall Ubuntu 8.04 or use another live cd of 8.10 to upgrade witch would work better?

I would do a clean install from the 8.10 live cd. You don't need to uninstall 8.04 just replace it with 8.10.

---

