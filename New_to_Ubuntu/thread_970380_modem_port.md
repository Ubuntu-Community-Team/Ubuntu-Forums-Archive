---
title: "modem port"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by theozzlives on 2008-11-04
how do I know what port my modem is on I tryed Device Manager, but it just says what my modem is

---

### Post by Mark_in_Hollywood on 2008-11-08
> **theozzlives said:**
> how do I know what port my modem is on I tryed Device Manager, but it just says what my modem is

this isn't enough information from you. We need to know the make, model and type (ISA, PCI, USB) device.

Have a look here:

Setting up Dial-up connection in Ubuntu
[http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html](http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html)

but if that isn't enough:

Try:

System/Administration/Network Tools. If you can find you device there it might say. I'm assuming you are referring to a dial-up modem.

If not, in a terminal, type

lspci

and next

lsusb

cut and paste the results here.

---

### Post by theozzlives on 2008-11-09
00:00.0 Host bridge: Silicon Integrated Systems [SiS] 620 Host (rev 02)
00:00.1 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev d0)
00:01.0 ISA bridge: Silicon Integrated Systems [SiS] SiS85C503/5513 (LPC Bridge) (rev b3)
00:01.1 Class ff00: Silicon Integrated Systems [SiS] ACPI
00:01.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.1 Controller (rev 11)
00:02.0 PCI bridge: Silicon Integrated Systems [SiS] Virtual PCI-to-PCI bridge (AGP)
00:06.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24/30 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
00:0a.0 Communication controller: Rockwell International HCF 56k Data/Fax/Voice/Spkp (w/Handset) Modem (rev 01)
00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:0c.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
00:0c.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
00:0c.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 65)
01:00.0 VGA compatible controller: Silicon Integrated Systems [SiS] 530/620 PCI/AGP VGA Display Adapter (rev 2a)

---

### Post by Mark_in_Hollywood on 2008-11-09
00:0a.0 Communication controller: Rockwell International HCF 56k Data/Fax/Voice/Spkp (w/Handset) Modem (rev 01)


Try this site:

[http://www.modemsite.com/56k/rockhcf.asp](http://www.modemsite.com/56k/rockhcf.asp)


get back to me here if that's no help.

---

### Post by theozzlives on 2008-11-10
I don't need all that, I just need my COM port so I can setup efax tp monitor my modem and answer when a call comes in.

---

### Post by Mark_in_Hollywood on 2008-11-12
> **theozzlives said:**
> I don't need all that, I just need my COM port so I can setup efax tp monitor my modem and answer when a call comes in.

Try the line below in the terminal:

netstat *a ¦ grep LISTEN

---

### Post by theozzlives on 2008-11-12
didn't do nothin

---

### Post by Mark_in_Hollywood on 2008-11-13
> **theozzlives said:**
> didn't do nothin

by which you mean there was no output to the screen? If there is no output whatever problems you have are way way beyond my knowledge. Sorry.

---

