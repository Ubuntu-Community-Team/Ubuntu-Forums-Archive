---
title: "Find, use older kernel on 15.10"
date: 2016-04-04
forum: New to Ubuntu
---

### Post by crip720 on 2016-04-04
I been having trouble with hard freezes on Ubuntu 15.10(OS stops working post) and most work arounds are not working.  I have read that the 4.1 kernel is stable.  My problem is that the 4.1 kernel only shows in update-grub.  It does not show on recovery boot, or in synpathics.  How can I find this kernel in the OS and see if it works?  I would prefer not to install it.  Recovery option only shows kernels 4.2 and 3.19 as does snypathics.  Thank you, Colin.

---

### Post by oldos2er on 2016-04-04
```
ls /boot
``` If it's there you'll see it listed.

---

### Post by crip720 on 2016-04-04
Is /boot shows 4.1, but seems to be missing vmlinuz efi.signed for 4.1.  Only has 4.1 vmlinuz generic.
crip@aspire1 ~> ls /boot
abi-3.19.0-49-generic                 memtest86+.bin
abi-4.1.6-040106-generic              memtest86+.elf
abi-4.2.0-27-generic                  memtest86+_multiboot.bin
abi-4.2.0-30-generic                  System.map-3.19.0-49-generic
abi-4.2.0-34-generic                  System.map-4.1.6-040106-generic
config-3.19.0-49-generic              System.map-4.2.0-27-generic
config-4.1.6-040106-generic           System.map-4.2.0-30-generic
config-4.2.0-27-generic               System.map-4.2.0-34-generic
config-4.2.0-30-generic               vmlinuz-3.19.0-49-generic
config-4.2.0-34-generic               vmlinuz-3.19.0-49-generic.efi.signed
efi/                                  vmlinuz-4.1.6-040106-generic
grub/                                 vmlinuz-4.2.0-27-generic
initrd.img-3.19.0-49-generic          vmlinuz-4.2.0-27-generic.efi.signed
initrd.img-4.1.6-040106-generic       vmlinuz-4.2.0-30-generic
initrd.img-4.2.0-27-generic           vmlinuz-4.2.0-30-generic.efi.signed
initrd.img-4.2.0-27-generic.old-dkms  vmlinuz-4.2.0-34-generic
initrd.img-4.2.0-30-generic           vmlinuz-4.2.0-34-generic.efi.signed
initrd.img-4.2.0-34-generic
crip@aspire1 ~> 
Is this the problem?  Thank you, Colin.

---

### Post by grahammechanical on 2016-04-04
If a kernel is listed in the update-grub printout it will also appear in Advanced options sub-menu both as a standard loading kernel & again as a kernel with recovery mode as part of the loading process.

I have a BIOS boot system motherboard and as would be expected I have an empty /boot/efi/ when it comes to kernels. But you have a kernel in /boot/efi/ and it is the 4.1.6 kernel. But none of the other kernels.

Are you in the strange situation of having Ubuntu installed in BIOS/legacy/CSM mode and one kernel installed in EFI mode? 

Regards.

---

### Post by crip720 on 2016-04-04
Had to install 15.04 in legacy mode, since that was the only way that the laptop would boot the DVD. Did change back to UEFI mode after and everything worked.  15.04 was upgraded(from software updater) to 15.10 with laptop in UEFI mode(secure boot off).  Recovery mode only shows about three 3.19 kernels and about three 4.2 kernels.  Synphatic only shows 3.19 and 4.2 kernels installed or available to install.  Is there a way to show or place the 4.1 kernel in the recovery section of grub?  Thank you, Colin.

---

