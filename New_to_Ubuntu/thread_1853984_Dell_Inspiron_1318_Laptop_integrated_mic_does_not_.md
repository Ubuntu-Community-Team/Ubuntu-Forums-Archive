---
title: "Dell Inspiron 1318 Laptop integrated mic does not work"
date: 2011-10-03
forum: New to Ubuntu
---

### Post by ubun2geek on 2011-10-03
Hi. I have a Dell Inspiron 1318 Laptop with an integrated mic that does not work in ubuntu (it does in windows)Here is the lspci info;
```
@ubuntupc:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)

```
Thanks!

---

### Post by anewguy on 2011-10-03
It appears that such problems with the 801H have been common for years.  Don't worry that the titles or descriptions of the following may not match what you are thinking - usually these problems are all common regardless of the symptom reported.

Here's an old launchpad bug report that has info in it for not using pulse audio:

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/261018]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/261018")

Here's a newer post regarding 10.04:

[http://askubuntu.com/questions/18547/built-in-microphone-not-detected]("http://askubuntu.com/questions/18547/built-in-microphone-not-detected")

Try those - I'll keep looking.  Remember - google is your friend:

ubuntu 11.04 82801h microphone in the search string......



Dave ;)

---

### Post by ubun2geek on 2011-10-04
Its a 1318 not a 801H.
Thanks!

---

### Post by anewguy on 2011-10-06
I was referring to the chip, not the model of the laptop.  The chip in question is an 82801H, as per your lscpi output:

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

Sorry if anyone got confused on that.

Dave ;)

---

### Post by ubun2geek on 2011-10-06
Thanks for clarifying that! Do you have an idea of how to fix this? I play guitar and would like to take advantage of all these awesome tools.

---

### Post by Toz on 2011-10-06
This might help: [http://ubuntuforums.org/showthread.php?p=9307284]("http://ubuntuforums.org/showthread.php?p=9307284").

---

### Post by ubun2geek on 2011-10-07
Thanks so much!
+1
Thanks to everyone else who helped, too.

---

