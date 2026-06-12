---
title: "42T0825 ThinkPad 11a/b/g/n Wireless LAN Mini Express Adapter Problems"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by CeBiff on 2008-08-31
Hey guys, i'm on a ThinkPad 11a/b/g/n Wireless LAN Mini Express Adapter.  I just installed Hardy Heron and out of the box I am able to detect networks, but am unable to connect.

Does anyone know how I can fix this problem?

Thank you a ton!

---

### Post by s1337m on 2008-08-31
Hi, please tell us your kernel vers, ubuntu vers and card specs.  To do this, go onto your windows (assuming dual boot) and its under accessories.

---

### Post by CeBiff on 2008-08-31
I'm not dualbooting, this is a Ubuntu only machine :D

---

### Post by anewguy on 2008-08-31
Post back the output of lspci.

Thanks.

---

### Post by CeBiff on 2008-08-31
```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HBM (ICH8M-E) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation Quadro FX 570M (rev a1)
03:00.0 Ethernet controller: Atheros Communications Inc. AR5212 802.11abg NIC (rev 01)
15:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev ba)
15:00.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 04)
15:00.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 21)
15:00.3 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 11)
15:00.4 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 11)
15:00.5 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 11)

```

---

### Post by anewguy on 2008-08-31
Okay, now we knoe the chipset, etc., of your wireless adaptor:

03:00.0 Ethernet controller: Atheros Communications Inc. AR5212 802.11abg NIC (rev 01)

Since it's really late, I won't be looking more at this until tomorrow or Monday.  However, if you want to, you can try searching this forum for Atheros AR5212 wireless and see if anything is returned.  You can also do the same type of search on Yahoo or Google via

Ubuntu Atheros AR5212 driver and see if anything comes up.

I'll look at it more later!

Dave  :)

---

### Post by anewguy on 2008-08-31
You'll need to go to this site for the Linux driver:

[http://madwifi.org/]("http://madwifi.org/")

---

### Post by CeBiff on 2008-08-31
> **anewguy said:**
> You'll need to go to this site for the Linux driver:

[http://madwifi.org/]("http://madwifi.org/")

So I downloaded the .tar.gz file... Where do I go from here?  Sorry, i'm an absolute beginner!

( ;; ^ 0^)

---

### Post by CeBiff on 2008-08-31
Er, are you sure I need the madwifi.org drivers?  It seems like they come built in with 8.04 and that's why I can detect networks, but I cna't connect to them...

---

### Post by CeBiff on 2008-08-31
I reset the router and now it's working.. I will keep you postd as to whether or not it is a stable connection.

---

### Post by CeBiff on 2008-08-31
Ok so, I can connect to WPA and I can get packets.  but as soon as i get about 3 feet away from the router, I stop getting packets.

What's up with that?

---

### Post by anewguy on 2008-09-01
Not sure what would cause a loss of signal at that short of distance.  Does your wireless have any type of "gain" control or radio on/off if used in Windows?

---

### Post by CeBiff on 2008-09-15
I'm not sure what you mean by that.

but yea, i can only use wifi if i'm in the same room as the router... which makes ubuntu kind of unusable :(

I really want to use ubuntu primarily.. anyone got any ideas?

---

