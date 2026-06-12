---
title: "Linux on Toshiba mini nb305-n310"
date: 2013-01-01
forum: New to Ubuntu
---

### Post by dg91 on 2013-01-01
Ok till now I installed like 8-9 linux distros on this netbook and every one of them have so many problems....(wifi dont work, suspend dont work, screen wont wake up from suspend, gestures on touchpad dont work like 2 finger scroll...etc)...

I managed to fix some of them but...some like wifi and touchpad just cant get to work...

so my question: have anybody found some ubuntu version that most of the things will work on this specific netbook (toshiba nb305-n310)?

I found on some forum that ubuntu 9.10 get along pretty good with this netbook so if anyone tryed some version of ubuntu that something will work I would really appreciate it.

If not ubuntu then maybe someone found some other linux distro that work with this netbook so really ....if you can help me in any way  pls ...thx

---

### Post by daslinkard on 2013-01-01
This [link]("http://ubuntuforums.org/showthread.php?t=1770647") may help you in search of finding the solution for your touchpad mouse.  As far as your wi-fi connection goes....what is the output of running the following terminal command
```
lspci
```

---

### Post by dg91 on 2013-01-01
output is :

00:00.0 Host bridge: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx DMI Bridge

00:02.0 VGA compatible controller: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller

00:02.1 Display controller: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller

00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 02)

00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 02)

00:1c.1 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 2 (rev 02)

00:1c.2 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 3 (rev 02)

00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 02)

00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 02)

00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 02)

00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 02)

00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 02)

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)

00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)

00:1f.2 IDE interface: Intel Corporation NM10/ICH7 Family SATA Controller [IDE mode] (rev 02)

00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 02)

07:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)


I can detect wifi card but I cant enable it with fn+f8 like on windows xp..

---

### Post by daslinkard on 2013-01-02
This link [here]("http://askubuntu.com/questions/67437/how-do-i-install-a-driver-for-an-atheros-ar9285") should walk you through on getting your wireless back.

---

