---
title: "grub error"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by chado52 on 2008-06-14
ok when i start up my computer i get a 
GRUB Loading stage 1.5.
GRUB loading, please wait...
Error 17
please help

---

### Post by JillSwift on 2008-06-14
That means Grub can't find its config file.

Tell us more about your setup and any recent software/OS changes to it. Specifically about your hard disks and other storage.

---

### Post by chado52 on 2008-06-14
what do you want to know?

---

### Post by JillSwift on 2008-06-14
> **chado52 said:**
> what do you want to know?
Well, like:
How many hard disks are on the machine?
Are they SATA, Paralel-ATA, USB, FireWire...?
Are you dual-booting and if so which operating systems?
Did you recently re-install or remove one of the operating systems?

Stuff like that.

---

### Post by chado52 on 2008-06-14
How many hard disks are on the machine?one 
Are they SATA, Paralel-ATA, USB, FireWire...?how do i tell?
Are you dual-booting and if so which operating systems?im dual booting. windows xp media edition, and ubuntu
Did you recently re-install or remove one of the operating systems?i barely re installed ubuntu

---

### Post by logos34 on 2008-06-14
reinstall grub to the MBR and the root partition:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Or use [Super Grub Disk]("http://supergrub.forjamari.linex.org/").

---

### Post by JillSwift on 2008-06-14
> **chado52 said:**
> How many hard disks are on the machine?one 
Are they SATA, Paralel-ATA, USB, FireWire...?how do i tell?
Are you dual-booting and if so which operating systems?im dual booting. windows xp media edition, and ubuntu
Did you recently re-install or remove one of the operating systems?i barely re installed ubuntuOk. Don't worry about what sort the disk is, since you've only the one it doesn't matter.

Check out [this thread]("http://ubuntuforums.org/showthread.php?t=224351") for information on how to re-install Grub. Once that's done, all should be well again.

---

