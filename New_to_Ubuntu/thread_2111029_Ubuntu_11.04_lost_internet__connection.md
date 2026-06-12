---
title: "Ubuntu 11.04 lost internet  connection"
date: 2013-01-31
forum: New to Ubuntu
---

### Post by Mikebartgeier on 2013-01-31
Hi! I installed Ubuntu 11.04 in my computer a long time ago and it was working like a charm until one day I could not connect to to the internet via ethernet. It is quite urgent, I need the internet connection to work!

ifconfig throws:
eth1      Link encap:Ethernet  HWaddr 1c:6f:65:c8:0e:8b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:42 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:375 errors:0 dropped:0 overruns:0 frame:0
          TX packets:375 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:19810 (19.8 KB)  TX bytes:19810 (19.8 KB)

lspci throws:
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation 2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 82801 PCI Bridge (rev b5)
00:1c.4 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 5 (rev b5)
00:1c.5 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 6 (rev b5)
00:1c.6 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 7 (rev b5)
00:1c.7 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 8 (rev b5)
00:1d.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation P67 Express Chipset Family LPC Controller (rev 05)
00:1f.2 RAID bus controller: Intel Corporation 82801 SATA RAID Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation GF110 [Geforce GTX 570] (rev a1)
01:00.1 Audio device: nVidia Corporation GF110 High Definition Audio Controller (rev a1)
03:00.0 PCI bridge: Integrated Technology Express, Inc. Device 8892 (rev 10)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
05:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)
06:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
08:00.0 IDE interface: Marvell Technology Group Ltd. Device 91a3 (rev 11)

dmesg | tail -n10 throws
[  104.939791] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[  104.940128] Console: switching to colour frame buffer device 200x75
[  104.940172] fb0: VESA VGA frame buffer device
[  104.967365] ppdev: user-space parallel port driver
[  104.977771] audit_printk_skb: 9 callbacks suppressed
[  104.977775] type=1400 audit(1359675145.467:15): apparmor="STATUS" operation="profile_replace" name="/usr/lib/cups/backend/cups-pdf" pid=1496 comm="apparmor_parser"
[  104.978978] type=1400 audit(1359675145.467:16): apparmor="STATUS" operation="profile_replace" name="/usr/sbin/cupsd" pid=1496 comm="apparmor_parser"
[  105.128301] ioremap error for 0xdf7a3000-0xdf7a4000, requested 0x10, got 0x0
[  107.337581] EXT4-fs (dm-5): re-mounted. Opts: errors=remount-ro,commit=0
[  108.804849] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.

Thanks!

---

### Post by Bucky Ball on 2013-01-31
Welcome to the forums.

Might be a good thing. 11.04 is no longer supported which means it gets no updates, including security updates. If the machine is online it may be vulnerable and could be compromised.

I would move to a supported release, perhaps 12.04 LTS which is stable and supported until April 2017.

Good luck.

PS: Can you go with a cable while you do what you have to do? After that I strongly advise moving to a supported release.

---

### Post by Mikebartgeier on 2013-02-05
Thank you! I think ill have to install 12.04 later but right now I trying to connect with a cable but my ethernet connections dont work :S

---

