---
title: "Can't connect using cable only Wifi. Unity user"
date: 2011-09-13
forum: New to Ubuntu
---

### Post by Peterfc on 2011-09-13
Hi All

Sorry for what seems a simple problem but after trying for what seems like ages i need help.

I have to use an Internet Cafe here in Portugal while i wait for my Adsl line to be installed. When i connect using a cat5 cable nothing happens. Wifi is fine but only when the staff who know what to do are on duty. 

Enable networking is ticked
Enable wireless   is ticked 

But i am sorry i don't know where to start to get the cable to be seen by the system. I am using Unity with all updates done.

I am using an Advent laptop 3GB ram 250Mb hard drive. 1.3 celeron 

Thanks for reading

---

### Post by gandaran on 2011-09-13
wired internet should just work, you don't have to do anything, plug the ethernet cable to computer and internet connects automatically.
if it doesn't then you could have an ethernet card driver problem but this would be a rare problem as almost every ethernet device works out of the box on linux
type in terminal this to find out the ethernet card brand and paste the output here.
```
lspci
```

---

### Post by Peterfc on 2011-09-13
Hi and thanks for the reply. I am sorry but the output means little to me. 

Peter

peter@Valeboa:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M-E LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller (rev 10)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
peter@Valeboa:~$

---

### Post by gandaran on 2011-09-13
> 04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
should work, no drivers needed, just check that DCHP server is enabled on the router configurations, connect cable and you should have an auto connection setup in network manager wired tab, if still no internet type in terminal (connected with cable)
```
ifconfig
```

---

