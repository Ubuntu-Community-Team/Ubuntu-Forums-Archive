---
title: "Wireless Problems"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by 1nflux on 2008-05-13
I am completely new to Linux and have a Dell Latitude 830. I have the intel 965 chipset and am trying to connect to a 2WIRE Homeportal1700 wirelessly. Every time I try to connect it resets the gateway and knocks all the computers in the house off of the internet. I am running Ubuntu 8.04 Hardy, but I am doing it through WUBI. How do I fix this and would it change anything if I did a full install of Ubuntu Hardy. I am trying to figure out if I want to make the jump to Ubuntu or not, but I'm not going to be able to if I can't have internet.

---

### Post by tamoneya on 2008-05-13
post the result of ```
lspci
```

---

### Post by 1nflux on 2008-05-13
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
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02) 
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02) 
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02) 
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02) 
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2) 
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02) 
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02) 
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 02) 
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02) 
03:01.0 CardBus bridge: O2 Micro, Inc. Cardbus bridge (rev 21) 
03:01.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02) 
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express (rev 02) 
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

---

