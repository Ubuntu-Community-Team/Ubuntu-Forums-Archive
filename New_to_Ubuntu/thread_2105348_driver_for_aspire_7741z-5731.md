---
title: "driver for aspire 7741z-5731?"
date: 2013-01-15
forum: New to Ubuntu
---

### Post by 101kitty on 2013-01-15
Were can i find drivers for driver for aspire 7741z-5731?

I'm trying to get my roommate to try out Ubuntu ^_^

---

### Post by westie457 on 2013-01-15
Could you be more specific about which drivers you need please.

In my experience with Acer Aspire laptops the only drivers I have had to hunt down are for the wireless chipset on one laptop and Nvidia drivers on the newer one.

---

### Post by 101kitty on 2013-01-15
Oops! Sorry about that, i need the graphics drivers and the drivers for the wireless, the wireless works its very slow and not working 100%

---

### Post by sandyd on 2013-01-15
Hi, can you post the output of
```

lspci
lsusb
ifconfig
```
please?

Thanks!

---

### Post by 101kitty on 2013-01-15
```
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
02:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe (rev 01)
04:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
nyke@ubuntu:~$ lsusb
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 003: ID 04f2:b1d8 Chicony Electronics Co., Ltd 
```This is what she said.

---

### Post by mastablasta on 2013-01-16
one thing is certain:
 
>  
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)


 
graphics drivers are already included in kernel.
 
as for the wi-fi have you tried connecting with cable to computer and selecting additonal drivers?

---

### Post by 101kitty on 2013-01-16
I'm using the cable right now, the wireless drivers do work but its really really slow... so I'm assuming its not using the proper drivers.

How do i chose different drivers for the wireless adpt?

---

### Post by kurt18947 on 2013-01-16
Is this a thread that solves a problem similar to yours?

[http://ubuntuforums.org/showthread.php?t=2073974&highlight=ath9k+nohwcrypt](http://ubuntuforums.org/showthread.php?t=2073974&highlight=ath9k+nohwcrypt)


There is an issue with some Atheros WiFi chipsets that have a pretty simple fix.  This may or may not work but it's something I'd try.  The file "ath9k.conf" probably doesn't exist.  You create it then save.  You can use gedit instead of nano if that's more familiar to you.


> 
On my Acer laptop I had to blacklist acer-wmi plus I had to do this:

     Code:
     sudo nano /etc/modprobe.d/ath9k.conf 
and add this line:

     Code:
     options ath9k nohwcrypt=1 
Save and reboot.

Worst case if it doesn't help is to delete the ath9k.conf file.  Or just leave it if it doesn't cause any problem.  I have a Netgear WNA1100 that would occasionally disconnect.  The above trick seems to have fixed the random disconnecting problem.

---

### Post by mastablasta on 2013-01-16
> **101kitty said:**
> How do i chose different drivers for the wireless adpt?
 
in 12.10 - they are in software center in software sources additional drivers.
in 12.04 the interface is called jockey and should pop up if any drivers exists. make sure you have additional repositories enabled (partners, nonfree and such...).

---

### Post by 101kitty on 2013-01-17
This help get it working, thanks all.

[http://ubuntuforums.org/showthread.php?t=2073974&highlight=ath9k+nohwcrypt](http://ubuntuforums.org/showthread.php?t=2073974&highlight=ath9k+nohwcrypt)

---

