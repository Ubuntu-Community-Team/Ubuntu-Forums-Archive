---
title: "Fail to access Windows 8.1 after install Ubuntu"
date: 2014-11-17
forum: New to Ubuntu
---

### Post by axiom2 on 2014-11-17
Hi, I recently tried installing Ubuntu 14.04 along with Windows 8.1

It worked well on the first 3 days as I can access both OS

until today I shut down Ubuntu and tried to access Windows it gives me error msg as below

"
Your PC needs to be repaired
The application or operating system could not be loaded because required files is missing or contains error

File: \\WINDOWS\system32\winload.efi
Error code : 0xc000000f
" 

I was provided three option, but none works

This is the result from boot repair

[http://paste.ubuntu.com/9052320/](http://paste.ubuntu.com/9052320/)


Additional Information, I can mount my windows partition, but I cannot view any files inside

Any idea how can I access my windows ?

---

### Post by oldfred on 2014-11-17
Did you leave Windows fast boot or always on hibernation set? That almost always causes issues and you then need your Windows repair flash drive to fix it. Boot-Repair only can fix minor Windows issues.

Are you trying to boot Windows from grub or directly from UEFI menu.
You seem to show two Windows entries in UEFI menu. 

      >  
BootOrder: 0000,0001,0002,0004,0005
Boot0000* ubuntu    HD(1,800,32000,89ec981c-30b6-4a84-b819-40c6703a6a1b)File(EFIubuntushimx64.efi)
Boot0001* Windows Boot Manager    HD(1,800,32000,89ec981c-30b6-4a84-b819-40c6703a6a1b)File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...}................
Boot0002* Windows Boot Manager    HD(2,32800,1c2000,30828e35-901b-4479-9e33-5cd50520c48b)File(EFIMicrosoftBootbootmgfw.efi)
Boot0004* ubuntu    HD(1,800,32000,89ec981c-30b6-4a84-b819-40c6703a6a1b)File(EFIUbuntugrubx64.efi)
Boot0005* UEFI: Generic Flash Disk 8.07    ACPI(a0341d0,0)PCI(14,0)USB(1,0)HD(1,2e0,79dd20,f3881c07)AMBO

Not sure what difference is, if any. Have you tried both from UEFI or perhaps one time boot key.
Do you have UEFI set to boot in UEFI mode not CSM/BIOS?
Both installs are in UEFI so I would not think you changed to CSM.

---

