---
title: "BIOS Won't Recognize Ubuntu HD"
date: 2012-08-12
forum: New to Ubuntu
---

### Post by Rabark on 2012-08-12
Bought a Seagate SATA hard drive today.  Plugged it into the motherboard.  Boot from CD to install Ubuntu 12.04 on it.

So now I have two hard drives.  Windows XP SP3 on the "old" one, Ubuntu 12.04 on the new one.

Ubuntu installer says it's done installing and needs to restart to put on the finishing touch.  Cool.  I click OK/restart/whatever.

Computer restarts . . . and boots XP. :(

So I figure I just need to redo the boot order in BIOS.  But BIOS only sees one SATA hard drive.  Not two.  Thinking myself clever, I power off, open my tower's case, unplug the Windows hard drive SATA cables and reboot.  Ha!  Now it has no choice but to boot up Ubuntu, right?  Right?

No boot device found.  Press F1 to retry, press F2 to enter Setup. :(

So somehow, BIOS can't see the new hard drive, but the live CD saw it just fine.  Any ideas how to get BIOS to play nice?

BIOS Version: Dell Inc 1.4.0
SMBIOS Version: 2.3

-Bob

---

### Post by deadflowr on 2012-08-12
Most likely, your GRUB wasn't installed correctly.

Follow this to help reset it:

[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

---

