---
title: "Network manager error/ wireless does not work"
date: 2012-03-10
forum: New to Ubuntu
---

### Post by adido on 2012-03-10
Hi,

I'm super new to Ubuntu, just finished my first install less than one hour ago, and ran into my first challenge.

I cannot connect to the wireless network, although the cable works just fine.

During the first steps of installing Ubuntu Studio I had an error that the network manager was not found (... or something similar). 

I've been reading some other threads ([http://ubuntuforums.org/showthread.php?t=1859689](http://ubuntuforums.org/showthread.php?t=1859689)) and tried the **lspci **command. Bellow are the results:

Can anyone please suggest a solution?
Cheers,
Adrian

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
02:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:09.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
0b:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)

---

### Post by wildmanne39 on 2012-03-10
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following command into it.
```
sudo apt-get install b43-fwcutter firmware-b43-lpphy-installer
```
then unplug wired connection and reboot and it should work if not we will have to dig deeper.
Thanks

---

### Post by adido on 2012-03-11
[]("http://ubuntuforums.org/member.php?u=508533")Thanks! I posted the question immediately after Ubuntu Studio finished installation. The next day, with the second boot, there was a message waiting for me regarding a Broadcom STA proprietary wireless driver that needed installation. That was it. Just needed a reboot :)

Many thanks for the help!

---

### Post by wildmanne39 on 2012-03-11
Hi, your welcome! I am glad it is working.

---

