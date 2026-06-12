---
title: "wifi radar detects signals, but cant get ip address."
date: 2008-06-11
forum: New to Ubuntu
---

### Post by WinterMadness on 2008-06-11
can anyone help me out here? I tried it with mac security/WEP key off and on (I never had the ethernet chord plugged in while trying to connect to the wireless either)

I just think its odd that it can detect but not connect. I think its some configuration i dont understand probably related to the program. but I dont know either. 

heres lspci just incase. not sure if you need it or not. 



00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
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
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400M GS (rev a1)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01)

---

### Post by burakerenn on 2008-06-11
Looks like my problem with my Atheros card with ndiswrapper. If you're using ndiswrapper try these in terminal

sudo modprobe -r ndiswrapper (unload ndiswrapper from modules)
sudo modprobe ndiswrapper    (loads ndiswrapper to modules again)

I still couldn't find a solution and have to do it everytime i boot my computer :(

---

### Post by WinterMadness on 2008-06-11
> **burakerenn said:**
> Looks like my problem with my Atheros card with ndiswrapper. If you're using ndiswrapper try these in terminal

sudo modprobe -r ndiswrapper (unload ndiswrapper from modules)
sudo modprobe ndiswrapper    (loads ndiswrapper to modules again)

I still couldn't find a solution and have to do it everytime i boot my computer :(

unfortunately that dosent work for me.
it weird how it can pick up any signal but not connect. do I need some kind package to make sure it connects?

---

### Post by Het Irv on 2008-06-11
I am haveing the same problem, do you have the Nvidia Restricted Drivers installed?

For me it seems if the drivers have never been installed on the system your fine, once the drivers have been installed, it craps out.  I have a bug report in.
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/237215](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/237215)

No one has answered yet...

---

### Post by WinterMadness on 2008-06-12
> **Het Irv said:**
> I am haveing the same problem, do you have the Nvidia Restricted Drivers installed?

For me it seems if the drivers have never been installed on the system your fine, once the drivers have been installed, it craps out.  I have a bug report in.
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/237215](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/237215)

No one has answered yet...



yeah i do, i guess its some kind of problem with Nvidia then? 
i wonder why that is. is there no way around this?

---

### Post by dmac71 on 2008-06-12
Thanks for that command string.  I have been trying to get my wireless with an Atheros card to work for over a month.  I used those two command strings and it works now.  I haven't shut down and rebooted to see if it would work then, but hey, any operation at all is a plus at this point.

---

