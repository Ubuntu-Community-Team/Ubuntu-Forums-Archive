---
title: "No sound"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by drkemprd on 2008-07-31
I'm pretty sure the laptop used a Crystal Audio sound card.. Saying theres no driver installed. Is it possible to use a generic driver or something?

---

### Post by drkemprd on 2008-07-31
Anyone?

---

### Post by buzzmandt on 2008-07-31
open terminal and type
> lspci

copy the results and post them here

---

### Post by drkemprd on 2008-07-31
> **buzzmandt said:**
> open terminal and type


copy the results and post them here

00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (AGP disabled) (rev 02)
00:02.0 CardBus bridge: Texas Instruments PCI1250 (rev 02)
00:02.1 CardBus bridge: Texas Instruments PCI1250 (rev 02)
00:03.0 VGA compatible controller: Neomagic Corporation NM2160 [MagicGraph 128XD] (rev 01)
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 01)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 01)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by prshah on 2008-07-31
> **drkemprd said:**
> I'm pretty sure the laptop used a Crystal Audio sound card.. Saying theres no driver installed. Is it possible to use a generic driver or something?

Take a look at these links:
[https://bugs.launchpad.net/suse/+bug/88527](https://bugs.launchpad.net/suse/+bug/88527) and
[http://ubuntuforums.org/showthread.php?t=114147](http://ubuntuforums.org/showthread.php?t=114147) especially the last post.

---

