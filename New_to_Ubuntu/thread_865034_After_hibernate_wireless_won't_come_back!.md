---
title: "After hibernate wireless won't come back!"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by Lori700698 on 2008-07-20
I have an annoying issue, our desktop is using wireless with a ndswrapper. On screen saver it comes back fine and when the screen is black (but you can still see light) comes back fine. But when the screen goes completely black (I'm assuming hibernate) wireless won't connect and you must reboot to make it work. The circles spin and we get a pop up box looking for passcode, type it all in and it just spins and never hooks up. On reboot don't have to do anything (passwords all saved in profiles), connects pretty quickly. Oh and this is all with Network Manager.

---

### Post by JagDragon on 2008-07-20
Unfortunately, this is a bug often encountered with ndiswrapper. If you really need to hibernate, I would recommend switching to a native linux driver. We can help you with that, just open up a terminal, type ```
lspci | grep Network
``` and post the output here.

---

### Post by Lori700698 on 2008-07-20
How can I switch to a native driver and still get my wireless to still work?  I am using a newly purchased and installed D-link extreme wireless for desktop.  Are there other drivers that will make this work?

---

### Post by JagDragon on 2008-07-20
> **JagDragon said:**
> Unfortunately, this is a bug often encountered with ndiswrapper. If you really need to hibernate, I would recommend switching to a native linux driver. We can help you with that, just open up a terminal, type ```
lspci
``` and post the output here.

If you do this, I can tell you if there are native drivers for your card or not ;)

---

### Post by Lori700698 on 2008-07-27
Sorry, I've been so busy between work and school and now football has started I haven't had time to sit at this computer.  Any way, here is the output, do I have any other options?

jake@ubuntu-JakePC:~$ lspci
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
05:00.0 Network controller: Atheros Communications Inc. AR5416 802.11abgn Wireless PCI Adapter (rev 01)
05:01.0 Communication controller: Conexant HSF 56k Data/Fax Modem
05:05.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61)
05:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller (rev 03)
jake@ubuntu-JakePC:~$

---

### Post by appi2012 on 2008-07-27
Run:
```
sudo modprobe ndiswrapper
```
in terminal to get your wireless back. (It should work)

---

### Post by gjoellee on 2008-07-27
you may also support this brainstorm idea: [http://brainstorm.ubuntu.com/idea/94/](http://brainstorm.ubuntu.com/idea/94/) and you should also add this bug to launchpad.net

---

### Post by stevoo on 2008-07-27
5676
..
well i think hibernate should be one of the most important thinks that need to be fixed. 

Eveyone is having pros with them

---

### Post by Lori700698 on 2008-07-27
I know for a fact it's the ndiswrapper giving me issues, I have an old wireless desktop connection that runs off the desktop and a USB cord, it's just a hassle using it with the extra cord and finding some where that it wont get knocked around.  I had to update our wireless to a D-link extreme because of PS3 connection issues, anyway I bought the coordinating wirelesses for the new system that installed right into the computer and eliminated the need for the desktop with wire.  When I plug the old desktop wireless in and disconnect the ndiswrapper the connection is better and the computer will come back after a nap.  Is there a native driver I can download and still use the newer installed wireless?

---

### Post by caljohnsmith on 2008-07-27
You have an Atheros AR5416 chipset, and the madwifi drivers work for most Atheros chipsets, but I don't know about that particular one--you'll have to check their documentation. 

I have the same type of issues as you using ndiswrapper when I suspend my computer. I solved it by modifying the Ubuntu suspend script to first remove ndiswrapper before doing anything else, and then on resume, I had it add back the ndiswrapper module. That works for me, and it might work for you with hibernate. I'm not sure, but I think the Ubuntu hibernate script is:
```
/usr/lib/hal/scripts/linux/hal-system-power-hibernate-linux
```
All you would have to do is add "modprobe -r ndiswrapper" at the beginning of the script right after "#!/bin/sh", and then "modprobe ndiswrapper" at the end, and see if that works.

---

