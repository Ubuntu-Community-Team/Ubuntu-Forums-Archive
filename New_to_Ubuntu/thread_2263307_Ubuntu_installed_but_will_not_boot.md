---
title: "Ubuntu installed but will not boot"
date: 2015-01-31
forum: New to Ubuntu
---

### Post by ansu2 on 2015-01-31
Hi,

I would first like to point that I am not a very advanced user, please keep that in mind. I have checked the forums but can't seem to find a fix that works for me.

I have installed ubuntu 14.04.1 LTS on a Acer Aspire V13 from USB. The computer came with only Linpus and I removed it during the ubuntu installation. The installation is (as far as I can tell) successfull but if I try to boot from the harddrive I get "No bootable device found". I can still boot from USB. I've tried pressing shift during start-up but can't seem to launch grub. I've run boot-repair but it did not fix my issue. 

Here is the report from boot-repair: [http://paste.ubuntu.com/9970813](http://paste.ubuntu.com/9970813)

Any help would be greatly appreciated, thanks!

---

### Post by fantab on 2015-01-31
You have UEFI. This is a new replacement for legacy BIOS. In a UEFI boot you have an ESP [EFI System Parttiion] where your boot files are. 
The legacy BIOS had boot files in MBR.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) : you MUST boot your Ubuntu DVD/USB in UEFI mode.. the link will show you how to tell the difference.

Reinstall Ubuntu in EFI mode.

---

