---
title: "How to forbid ssd access?"
date: 2022-07-14
forum: New to Ubuntu
---

### Post by keebz96 on 2022-07-14
Hi not sure where this goes, but my problem started when trying to  get my 32 bit laptop to boot from a usb with ubuntu installed ( i know it isnt a great option but i like the convienence) but it wont recognize it because it was created with a 64 type architecture (at least this is what it seems to be)

So i came across a command on a site  that said  it would install and allow support that architecture, however it installed the grub to my windows boot loader on my ssd and removed it from the usb making it a lock and key situation.  I cant find any way online to fix it in the os so im just reinstalling  and moving files over.

So my question is how do i stop this from happening again?   I was under the assumption unmounted meant it wouldnt use that drive.  Is there a way to take away that access without removing the ssd all together?

---

### Post by grahammechanical on 2022-07-14
There are some things that you need to understand. A 32 bit version of Ubuntu will run on a 32 bit CPU and a 64 bit CPU. This is because the 64 bit CPU was designed to be backwards compatible with 32 bit operating systems. But a 64 bit version of Ubuntu will not run on a 32 bit CPU. Also, 32 bit versions of Ubuntu are no longer available and have not been for some years.

When installing Ubuntu to a second drive, whether internal or external, the installer will default to installing the boot loader on the first drive unless we specifically instruct the installer to put the boot loader on the second drive.

In your case the boot loader's primary code is on the first drive but its configuration files are on the second drive. Which is fine so long as the second is still plugged in.

Regards

---

### Post by Impavidus on 2022-07-14
If you install in UEFI mode (recommended, but sometimes not available on hardware older than 10 years), the bootloader will be put on the EFI partition of the first hard drive, where the Windows bootloader is too. Both bootloaders (grub and the Windows bootloader) will happily exist alongside each other. If you have multiple harddrives, there are some tricks to get it on the other drive.

If you install in legacy mode, there can be only one bootloader per drive.

---

