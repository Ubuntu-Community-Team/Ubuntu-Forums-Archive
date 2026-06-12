---
title: "VirtualBox Bootloader"
date: 2009-07-08
forum: Programming Talk
---

### Post by 2words4uready on 2009-07-08
Is it possible to run just a bootloader in VirtualBox?
I have found some NASM sources of a bootloader and they say to write to a floppy etc. If possible how can i boot it in VirtualBox?

---

### Post by Nuticulus on 2009-07-08
Assuming you are using version 3.0.0 (other versions may be different), first create a virtual machine. It won't need a hard disk. Once you have created your virtual machine, click Settings, go to the System tab on the left, and make sure that Floppy is at the top in the Boot Order list. If not, change it.

Now click the Floppy tab on the left, click "Mount Floppy Drive", choose "Image file", browse to and select your image file, and click Ok.

Good luck! ;)

---

### Post by 2words4uready on 2009-07-08
Alright. Thanks :P

---

### Post by Nuticulus on 2009-07-08
No problem! In fact, if you already have a virtual machine, you can just mount the floppy on that one, without creating a new one.

Alternatively, when you are booting a virtual machine with the floppy mounted, you can press F12 at the Virtualbox splash screen, and you will be able to choose a device to boot from.

---

