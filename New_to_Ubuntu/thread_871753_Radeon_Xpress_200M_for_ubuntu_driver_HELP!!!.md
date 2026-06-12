---
title: "Radeon Xpress 200M for ubuntu driver HELP!!!"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by appoloin on 2008-07-27
Hi Fellow Ubuntu users!

Need Expert advice on finding a driver for Radeon Xpress 200M. I tried google but failed horribly.

Need to run #D on my laptop but need driver PLease Help..

See Bellow:
00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
03:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
03:06.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
03:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by UbuntuNerd on 2008-07-27
try this ,System>>Administration>>Restricted Drivers Manager.
Check the box for ATi Accelerated Graphics Driver.Let Ubuntu handle the rest post the result if you don't get it working.

---

### Post by overdrank on 2008-07-27
> **appoloin said:**
> Hi Fellow Ubuntu users!

Need Expert advice on finding a driver for Radeon Xpress 200M. I tried google but failed horribly.

Need to run #D on my laptop but need driver PLease Help..

See Bellow:
00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
02:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
03:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
03:06.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
03:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

Hi and welcome you may look at this thread for some help
[http://ubuntuforums.org/showthread.php?p=5462557#post5462557](http://ubuntuforums.org/showthread.php?p=5462557#post5462557)

---

### Post by Troll_the_Great on 2008-07-27
> **jperez78 said:**
> try this ,System>>Administration>>Restricted Drivers Manager.
Check the box for ATi Accelerated Graphics Driver.Let Ubuntu handle the rest post the result if you don't get it working.

If that doesn't work install EnvyNG and it will install the driver for you.
Type in a terminal:
```
sudo apt-get install envyng-gtk
```
After that you will find it under Applications-System Tools.
Hope this helps, and post back the results.
Cheers!

---

### Post by appoloin on 2008-07-27
thank you for reply., i dont have Restricted Drivers Manager on the list..

---

### Post by Troll_the_Great on 2008-07-27
> **appoloin said:**
> thank you for reply., i dont have Restricted Drivers Manager on the list..

Try with Envy then, it might work.

---

### Post by halitech on 2008-07-27
If you are installing Hardy then its called something else but it is under System - Admin - ???? (should say something about hardware, don't have Hardy on this machine)

---

### Post by Troll_the_Great on 2008-07-27
> **halitech said:**
> If you are installing Hardy then its called something else but it is under System - Admin - ???? (should say something about hardware, don't have Hardy on this machine)

It should be under System-Administration-Hardware Drivers.

---

### Post by halitech on 2008-07-27
thanks Troll, didn't want to fire up the laptop to check it for sure :)

---

### Post by Troll_the_Great on 2008-07-27
> **halitech said:**
> thanks Troll, didn't want to fire up the laptop to check it for sure :)

No problem ;)

---

