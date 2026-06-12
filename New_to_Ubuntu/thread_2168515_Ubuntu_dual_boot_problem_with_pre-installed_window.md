---
title: "Ubuntu dual boot problem with pre-installed windows 8"
date: 2013-08-18
forum: New to Ubuntu
---

### Post by cyrus2 on 2013-08-18
Hi guys,
I have  a new HP 2000 Laptop that came with pre-installed windows 8. I have tried to dual boot but my efforts have been futile. I have followed step by step procedures during the installation process and have done boot-repaird thrice all to no avail. I urgently need ur help because i think my problem is perculier to me sinec i have followed all posible tuts.

Please find in this thread the bootinfo URL

[http://paste.ubuntu.com/5993845/](http://paste.ubuntu.com/5993845/) 


Thanks in advance for helping me.

---

### Post by oldfred on 2013-08-18
BootInfo report looks normal.
You have both grub & Windows efi files in efi partition. And you have installed the signed versions of Ubuntu kernels. So you should be able to boot with secure boot on or off.
Some HPs seem to have UEFI on as secure boot on, and CSM/BIOS meaning to boot in UEFI mode if an efi partition found with boot files, if not the try to boot in BIOS mode from MBR. You  have no boot files in protective MBR, so only UEFI booting.
You should be able to choose ubuntu from UEFI menu.

Boot-Repair has extracted UEFI boot choices.

>  BootOrder: [COLOR=#ff0000]3001[/COLOR],3002,3003,2001,2002,2003
Boot0001* Windows Boot Manager    HD(2,c8800,82000,23e7ff3e-5d13-42ce-8176-34f26b84558a)File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...0................
Boot0002* [COLOR=#0000ff]ubuntu[/COLOR]    HD(2,c8800,82000,23e7ff3e-5d13-42ce-8176-34f26b84558a)File(EFIubuntushimx64.efi)
Boot0003* [COLOR=#ee82ee]Ubuntu [/COLOR]   HD(2,c8800,82000,23e7ff3e-5d13-42ce-8176-34f26b84558a)File(EFIubuntugrubx64.efi)RC
Boot2001* USB Drive (UEFI)    RC
Boot2002* Internal CD/DVD ROM Drive (UEFI)    RC
Boot[COLOR=#ff0000]3001[/COLOR]* Internal Hard Disk or Solid State Disk    RC
Boot3002* Internal Hard Disk or Solid State Disk    RC
Boot3003* Internal Hard Disk or Solid State Disk    RC



this says you default is the hard drive, but you need to change to ubuntu or 0002 which is shim or secure boot, or 0003 which is grub which may just be UEFI without secure boot.

---

