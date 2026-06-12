---
title: "Lost internet"
date: 2012-01-30
forum: New to Ubuntu
---

### Post by afanasiew on 2012-01-30
Used Ubuntu 10.04 64 bit on my pc as a newbie for about 6 months, then lost cable internet connection following an auto update. Tried various suggestions from forums, all to no avail, so formatted hard drive and re-installed 10.04. No internet. Used laptop (wireless Windows XP on the same router) to download 11.10 32 bit ISO and installed that. Still no internet.
I really want to continue with Ubuntu, but may have to switch to Windows 7 if I can't get back online. The problem seems to be a common one, so is there a clear and straightforward fix in place please?

---

### Post by cortman on 2012-01-30
> **afanasiew said:**
> Used Ubuntu 10.04 64 bit on my pc as a newbie for about 6 months, then lost cable internet connection following an auto update. Tried various suggestions from forums, all to no avail, so formatted hard drive and re-installed 10.04. No internet. Used laptop (wireless Windows XP on the same router) to download 11.10 32 bit ISO and installed that. Still no internet.
I really want to continue with Ubuntu, but may have to switch to Windows 7 if I can't get back online. The problem seems to be a common one, so is there a clear and straightforward fix in place please?

This is the wired connection? Can we have some info on your PC? Also run

```
lspci
```

in a terminal and post the results.

---

### Post by hopelessone on 2012-01-30
click that up & down arrow on the top bar next to the time, and see if there is 2 connections, click one or the other, then afterwards delete the non working connection..

---

### Post by afanasiew on 2012-01-31
Thank you. Yes it is a wired connection.
Intel Core 2 Quad cpu [EMAIL="Q8300@2.50GHz"]Q8300@2.50GHz[/EMAIL] x4, 3.4GiB memory.
 
[EMAIL="ubuntu@ubuntu:~$"]ubuntu@ubuntu:~$[/EMAIL] lspci
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
 
I did not install 11.10 but ran it from disc due to lack of internet.

---

### Post by cortman on 2012-01-31
> **afanasiew said:**
> 
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)


It looks like this is a kernel update problem. See posts 4 & 5 of [this thread]("http://ubuntuforums.org/showthread.php?p=10283670"). It looks like the manufacturer has drivers for Linux available. Or else it may just be a reboot fix.

---

### Post by afanasiew on 2012-02-04
> **cortman said:**
> It looks like this is a kernel update problem. See posts 4 & 5 of [this thread]("http://ubuntuforums.org/showthread.php?p=10283670"). It looks like the manufacturer has drivers for Linux available. Or else it may just be a reboot fix.
 
*It looks like this is a kernel update problem. See posts 4 & 5 of *[[COLOR=#444444]*this thread*[/COLOR]]("http://ubuntuforums.org/showthread.php?p=10283670")*. It looks like the manufacturer has drivers for Linux available. Or else it may just be a reboot fix.*
 
Thanks, Cortman. I have downloaded and unpacked the appropriate compressed file from Realtek, BUT, I unpacked it in my folder, not in the file system. I've then done *cd r1000_v1.07* as per *readme* file, but unfortunately, as a newbie, I am unable to follow the rest of the *readme* file, which seems to assume more familiarity with linux than I possess. Can you please help me with:
 
Change to the directory:
cd r1000_vX.YZ
 
If you are running the target kernel, then you should be able to do :
make clean modules (as root or with sudo)
make install
depmod -a
<Force Link Status>
1. Force the link status when insert the driver.
If the user is in the path ~/r1000, the link status can be forced to one of the 5 modes as 
following command.
#insmod ./src/r1000.o speed=SPEED_MODE duplex=DUPLEX_MODE autoneg=NWAY_OPTION,
where
SPEED_MODE 
= 1000 for 1000Mbps
= 100 for 100Mbps 
= 10 for 10Mbps
DUPLEX_MODE
= 0 for half-duplex
= 1 for full-duplex
NWAY_OPTION
= 0 for auto-negotiation off
= 1 for auto-negotiation on
For example:
#insmod ./src/r1000.o speed=100 duplex=0 autoneg=0
will force PHY to operate in 100Mpbs Half-duplex.
2. Force the link status by using ethtool.
a. Insert the driver first.
b. Make sure that ethtool exists in /sbin.
c. Make sure that the eth? is up. If eth? is not up, use the following commond.
#ifconfig eth? up
d. Force the link status as the following command.
#ethtool -s eth? speed SPEED_MODE duplex DUPLEX_MODE autoneg NWAY_OPTION,
where
SPEED_MODE
= 1000 for 1000Mbps
= 100 for 100Mbps
= 10 for 10Mbps
DUPLEX_MODE
= half for half-duplex
= full for full-duplex
NWAY_OPTION
= off for auto-negotiation off
= on for auto-negotiation on
 
Your help is much appreciated.
 
afanasiew
 
Update - re-installed 10.04 64-bit and learned to move the r1000 directory using *sudo*, but didn't know where to move it to.

---

