---
title: "Help getting internet working"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by kslinux on 2008-11-24
I am new to linux.

I am trying to get the internet to work on an old desktop computer - Dell Dimension 4500.  I am using kubuntu 8.04.1 which uses KDE 3.5.9.

I have tried connecting the ethernet port of the Dell Dimension into the back of my Linksys wireless router (which has four available ethernet ports).  Kubuntu didn't recognize the computer's ethernet port.

I am currently using a Windows XP laptop for my internet.  I'd like to get the desktop working to try it out as well on the internet.  I have a wireless network at home.

I have plugged a Linksys WUSB54GSC wireless card into the desktop.  It would be ideal to get the wireless running if at all posible.

I've been reading on the forum what information is required.  I am posting the results from the common commands (i.e., lspci, iwconfig, ifconfig).  I have also posted the results from "lsusb".  This does show that the Linksys card is there.  Note also that "lsusb" shows an external hard drive and mouse installed.  Both of these work.

Thank you for your help.


Results from “lspci”:

00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 11)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 11)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Rage 128 Pro Ultra TF
02:01.0 Modem: Broadcom Corporation BCM4212 v.90 56k modem (rev 02)
02:02.0 Ethernet controller: Davicom Semiconductor, Inc. 21x4x DEC-Tulip compatible 10/100 Ethernet (rev 31)


Results from “iwconfig”:
lo        no wireless extensions.

eth0      no wireless extensions.


Results from “ifconfig”:
eth0      Link encap:Ethernet  HWaddr 00:08:a1:0d:53:8c
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 Base address:0xd800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


Results from “lsusb”:
Bus 004 Device 004: ID 1058:1100 Western Digital Technologies, Inc.
Bus 004 Device 002: ID 13b1:0026 Linksys
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
Bus 001 Device 001: ID 0000:0000

---

### Post by Olivier2371 on 2008-11-24
hi there,

You would have had better help if you'd posted in the networking part of the forum.

Personally I am not sure if I will be able to help you.

---

### Post by kslinux on 2008-11-26
I have waited over a day.  I can be patient.  With Olivier2371's comment, how long do I need to wait until I repost in a different part of the forum?

Please understand that I am new and am trying to follow forum rules and expectations.  If I need to wait --- I can do that!

Thanks

---

