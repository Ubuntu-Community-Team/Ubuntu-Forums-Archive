---
title: "wireless adapter emachines em250 not working on Ubuntu 12.10"
date: 2013-02-25
forum: New to Ubuntu
---

### Post by bilalx2 on 2013-02-25
Hi,

I am very new to ubuntu and have four issues for which i need help from expert guys here:

[LIST=1]
[*]I have installed ubuntu 12.10 without a network connection on my emachines em250 netbook. Now the wifi is not working. The green light of Wireless adapter is also not lit. Could someone tell me how to find out the wireless adapter and how and from where to download the driver.
[*]where exactly is the device manager in Ubuntu and how to reach it?
[*]My impression was that after i install Ubuntu, my netbook will start working fast, atleast faster than my windows 7 which was a major pain after one a half year of installation. But my machine is not working fast enough, like it used to when win7 was installed for the first time. can anyone suggest how to improve its performance.
[*]How can i improve the performance of my synaptic pointing device? it is extremely slow.
[/LIST]
Please forgive me if these questions are tooo basic. Thanks!

---

### Post by cariboo on 2013-02-27
To find out what you wireless device is as well as the rest of your hardware, open a terminal and type the following command:

```
lspci
```

and paste the output in your next post. We need to know what hardware your system has before being able to help you.

---

### Post by bilalx2 on 2013-02-27
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
bilal@bilal-eM250:~$

---

