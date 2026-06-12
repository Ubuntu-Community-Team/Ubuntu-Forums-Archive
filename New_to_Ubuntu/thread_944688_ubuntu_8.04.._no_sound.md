---
title: "ubuntu 8.04.. no sound"
date: 2008-10-11
forum: New to Ubuntu
---

### Post by rishabh.bitsgoa on 2008-10-11
hi,
i recently installed ubuntu 8.04... i previously had 7.10
the sound worked fine for 7.10 , but there is no sound in 8.04.
i searched on net... n i installed linux-image-2.6.24-19-i386,
linux-ubuntu modules-2.6.24-19-i386,linux-restricted modules-2.6.24-19-i386,
linux-2.6.24-19-i386, and linux-image-i386.
still no sound is coming. the /dev/snd dir is there with two files in it.
i dont know wat to do... i have a dual boot, n the sound works fine in windows xp.
my laptop is a compaq one.
please help. thank you.

PS: there is a red cross on the sound icon on the top right toolbar.
on clicking it gives..."no volume control GStreamer plugins and/or devices found"..

---

### Post by loboc on 2008-10-11
[URL="http://ubuntuforums.org/showpost.php?p=5638028&postcount=4"]This post has the bare minimum steps of trouble shooting a soundcard
[/URL]
[http://ubuntuforums.org/showpost.php?p=5638028&postcount=4](http://ubuntuforums.org/showpost.php?p=5638028&postcount=4)

---

### Post by rishabh.bitsgoa on 2008-10-11
lspci gives:
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
08:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)
08:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
08:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
08:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 0a)
08:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 05)
08:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)


sysinfo:
intel corporation 82801G(ICH7 family) High Definition Audio Controller(rev 02)
Subsysytem" Hewlwtt-Packard company Unknown device 30b2

lspci -v
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
        Subsystem: Hewlett-Packard Company Unknown device 30b2
        Flags: bus master, fast devsel, latency 0
        Memory at d4280000 (32-bit, non-prefetchable) [size=512K]
	Capabilities: <access denied>

---

### Post by rishabh.bitsgoa on 2008-10-11
on doing aplay -L , nothing comes up
and on doin sudo modprobe snd-82801G.. it gives
FATAL: Module snd_82801G not found.

 please help.

---

### Post by markbuntu on 2008-10-11
If you are having problems with the HDA card/chip on your laptop or one of these:

HD Audio (ICH6, ICH6M, ESB2, ICH7, ICH8 ),
		ATI SB450, SB600, RS600,
		VIA VT8251/VT8237A,
		SIS966, ULI M5461

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

You can also look here (look through the entire thread if the OP does not fix your problem , people have posted solutions for many specific machines):

[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

[http://ubuntuforums.org/showthread.php?t=820959](http://ubuntuforums.org/showthread.php?t=820959)

If you are having problems with headphone/speaker control with your HDA sound device you can try this thread:

[http://ubuntuforums.org/showthread.php?t=806620](http://ubuntuforums.org/showthread.php?t=806620)

For more extensive help and general sound troubleshooting:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

