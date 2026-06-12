---
title: "Unable to get the Grub Menu on the Starting the System"
date: 2014-02-12
forum: New to Ubuntu
---

### Post by suresh1163 on 2014-02-12
I have an HP 8300 SFF with Win 8 Pro. Wanted to try out Ubuntu 13.10. Installed and wanted dual boot to work. I have tried numerous attempts with boot repair but somehow unable to get the grub menu on start up.

[http://paste.ubuntu.com/6920735/](http://paste.ubuntu.com/6920735/)

Can some please tell where am I going wrong / why I am unable to get the grub menu

Thanks in advance

Suresh

---

### Post by deadflowr on 2014-02-12
What are you currently booting into, Win8 or Ubuntu?

---

### Post by suresh1163 on 2014-02-12
Windows 8 is automatically booting up

---

### Post by oldfred on 2014-02-12
Some vendors modify UEFI to only boot Windows. From UEFI menu can you boot ubuntu entry?
This should be the boot options you see.
> BootOrder: 0000,0003,0008,0007,0001,0002,0004,0005,0006
Boot0001* DTO UEFI USB Floppy/CD
Boot0002* DTO UEFI USB Hard Drive
Boot0003* DTO UEFI ATAPI CD-ROM Drive
Boot0004  CD/DVD Drive
Boot0005  DTO Legacy USB Floppy/CD
Boot0006  Hard Drive
Boot0007* Windows Boot Manager
Boot0008* HL-DT-ST DVDRAM GH24NSB0
Boot0000* ubuntu

---

