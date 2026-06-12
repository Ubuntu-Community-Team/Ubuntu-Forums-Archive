---
title: "Create Bootable Floppy Image"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by ElvetPuff on 2008-07-16
Hey,

I'm trying to make a bootable floopy disk image, but I can't find a good guide to do it.

I've compiled a small, toy, bootloader which is exactly 512 bytes in size.

I use dd to make a floppy image:

dd if=/dev/zero of=floppy.img bs=512 count=2880

But how do I get the bootloader to be the first 512 bytes of the image?

Cheers,

ElvetPuff

---

### Post by lazyart on 2008-07-16
does dd work with floppy disks?

dd if=floppy.img of=/dev/floppy

(don't know what device the floppy drive is.. just taking a stab here)

---

### Post by logos34 on 2008-07-16
Here's how to make a Grub bootloader floppy:
[https://help.ubuntu.com/community/GrubHowto/BootFloppy](https://help.ubuntu.com/community/GrubHowto/BootFloppy)

---

### Post by drs305 on 2008-07-16
Here's an easy way to make a bootable floppy. Install StartUp-Manager - there is a floppy option. In addition, you will get a gui app that will easily and safely allow you to edit the grub menu options and displays.

To install:
```
sudo aptitude install startupmanager
```

To create a bootable floppy:
System > Admininstration > StartUp-Manager > Advanced > Create Rescue Floppy

To learn more about StartUp-Manager:
[HOWTO: Grub Menu Kernel Display Options & StartUp-Manager]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by ElvetPuff on 2008-07-16
I forgot to add:

1) I do not have a floppy drive
2) I am trying to make a floppy image which contains the bootloader that I have compiled

Thanks,

ElvetPuff

---

### Post by lazyart on 2008-07-17
Well, i think what you have would work.  With no floppy drive, what do you plan to do with it?
You could create a virtual machine and use the image as a boot floppy and see if it works...

---

