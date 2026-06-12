---
title: "Dell Vostro 1500 Wireless Help Request"
date: 2008-09-27
forum: New to Ubuntu
---

### Post by sggrams on 2008-09-27
I have a dell vostro 1500 that my friend installed Ubuntu 8.04 on.  I have a wireless router but cannot get wireless service.  I can only connect to the internet through wired.  When I disconnect my wired the wireless service comes up and asks for my key code, I enter it but nothing happens.  I have search the forums and found similar issues but the steps to solving the problems are too complex for me.  I don't even know how to install something once I have downloaded it and I keep trying to fix it in the terminal but the messages in the threads always lead to another thread which I don't understand.  
I fear by now I have installed a lot of starter fixes but no finished product.
I would appreciate it if someone walked me through each step of fixing this problem.
Thank you.
Here is my information if this helps:
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)

00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)

00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)

00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)

00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 02)

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)

03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)

03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)

03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)

03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)

03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)

0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

sggrams@sggrams-laptop:~$ lsusb

Bus 007 Device 057: ID 05ac:1205 Apple Computer, Inc. iPod Mini 1.Gen/2.Gen

Bus 007 Device 001: ID 0000:0000  

Bus 006 Device 001: ID 0000:0000  

Bus 005 Device 001: ID 0000:0000  

Bus 004 Device 001: ID 0000:0000  

Bus 003 Device 001: ID 0000:0000  

Bus 002 Device 001: ID 0000:0000  

Bus 001 Device 006: ID 0a5c:4503 Broadcom Corp. 

Bus 001 Device 005: ID 0a5c:4502 Broadcom Corp. 

Bus 001 Device 004: ID 413c:8126 Dell Computer Corp. 

Bus 001 Device 003: ID 0a5c:4500 Broadcom Corp. 

Bus 001 Device 001: ID 0000:0000

---

### Post by h218design on 2008-10-05
sggrams, I have the same laptop, I'm no Linux/Ubuntu guru but I've been able to get my Vostro 1500 up and running.

Now let's see:  it sounds like you haven't enabled the preprietary drivers.

menu:system:administration:hardwaredrivers

You should see the broadcom driver listed there.  Select it, and reboot... I think this is all I have had to do since 7.10 to get my 1500's wireless up and working.  Also, before you reboot, I recommend downloading wicd (wicd.sourceforge.net) and installing it as your network manager... it works great.  just download the file (the .deb version) to your desktop then double click on it like an .exe file in windows. It'll bring up the .deb installer and take care of all the dependencies just like synaptic.

good luck with the vostro 1500.

---

