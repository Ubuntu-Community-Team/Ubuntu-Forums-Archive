---
title: "wireless adapter emachines em250 not working on Ubuntu 12.10"
date: 2013-03-01
forum: New to Ubuntu
---

### Post by bilalx2 on 2013-03-01
Hi, my wireless connections are not working after installing ubuntu. Can any one help?

Also i would like to know how to reach Device Manager in Ubuntu?

bilal@bilal-eM250:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GSE Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GSE Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [AHCI mode] (rev 02)
00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 02)
01:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
03:00.0 Ethernet controller: Atheros Communications Inc. AR8132 Fast Ethernet (rev c0)
bilal@bilal-eM250:~$ ^C
bilal@bilal-eM250:~$ 

Thanks

---

### Post by sully101 on 2013-03-02
Easiest way is to plug it into a network then System => Additional drivers, from memory there may be two optons for the chipset you have.

Theres further infomation here [http://askubuntu.com/questions/33855/how-do-i-get-a-broadcom-bcm4312-wireless-card-to-work]("http://askubuntu.com/questions/33855/how-do-i-get-a-broadcom-bcm4312-wireless-card-to-work") and here [http://askubuntu.com/questions/80402/broadcom-bcm4312-not-working]("http://askubuntu.com/questions/80402/broadcom-bcm4312-not-working")

---

