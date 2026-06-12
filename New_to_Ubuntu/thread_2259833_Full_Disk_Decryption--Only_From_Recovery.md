---
title: "Full Disk Decryption--Only From Recovery"
date: 2015-01-07
forum: New to Ubuntu
---

### Post by Yosef_Karo on 2015-01-07
[B]Near by lightning caused power to drop for a few seconds.  Was unable to decrypt HDD from the 'start page'.  Kept getting 'wrong password...'  From recovery I was finally able to decrypt and log on.  I'm concerned about rebooting to see if the problem persists; I am assuming that something is 'borked'.
[/B]
OS: Ubuntu 14.04 LTS 32-bit

Mother Board: Gigabyte GA-G41M-ES2L  no version so V.1
CPU:              Intel Dual Core E2220 2.4GHz
HDD:             Samsung HD502HJ

output from lspci:

ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 2 (rev 01)
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation NM10/ICH7 Family SATA Controller [IDE mode] (rev 01)
00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 01)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 02)
03:00.0 PCI bridge: Pericom Semiconductor PI7C8140A PCI-to-PCI Bridge
04:0c.0 Multimedia controller: Philips Semiconductors SAA7134/SAA7135HL Video Broadcast Decoder (rev 01)
04:0d.0 Multimedia controller: Philips Semiconductors SAA7134/SAA7135HL Video Broadcast Decoder (rev 01)
04:0e.0 Multimedia controller: Philips Semiconductors SAA7134/SAA7135HL Video Broadcast Decoder (rev 01)
04:0f.0 Multimedia controller: Philips Semiconductors SAA7134/SAA7135HL Video Broadcast Decoder (rev 01)

---

### Post by ajgreeny on 2015-01-07
Make sure that you backup everything from recovery mode before you try rebooting, just in case.

It may also be worth running a filesystem check, by using a live system and command ```
sudo e2fsck /dev/sdx#
``` on whatever is your root partition, and again separately on the /home partition, if you have one.  However, I have no idea how, or if, encryption will have any effect on the use of e2fsck; I have never encrypted anything on my systems.

Hopefully having got into the system from recovery-mode, you will now be able to do so from a normal bootup.

---

### Post by Yosef_Karo on 2015-01-09
All working fine now, thanks!

---

