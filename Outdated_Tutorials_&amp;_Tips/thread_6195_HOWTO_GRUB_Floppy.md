---
title: "HOWTO: GRUB Floppy"
date: 2004-11-25
forum: Outdated Tutorials &amp; Tips
---

### Post by wallijonn on 2004-11-25
How to create a bootable GRUB floppy:

If needed:
Start a Root Terminal
```

sudo gedit /etc/fstab
/dev/fd0        /media/floppy0  ext2,vfat    rw,user,noauto  0       0

```

{exit gedit / save}
{reboot}

-----------------------------------------------------------------------------------------------------

Insert a blank floppy
[COLOR=Red]Applications -> System Tools -> Floppy Formatter[/COLOR]
Choose "[COLOR=Red]Linux Native (ext2)[/COLOR]"

Start a Root Terminal
```

mkfs /dev/fd0
mount /media/floppy0
mkdir -p /media/floppy0/boot/grub
cp /boot/grub/stage1 /boot/grub/stage2 /boot/grub/menu.lst /media/floppy0/boot/grub
umount /media/floppy0

```

{reboot & set BIOS to boot from floppy first. It should read / boot from floppy}

---

### Post by ghoat on 2005-02-24
I'll give it a whirl.  Thanks.

---

### Post by catlett on 2006-05-21
I don't know if your still around but thank you!!! Someone just directed me to your link and I finally created a grub floppy.


Much obliged if your still around. 
Regards, Catlett

---

### Post by ghoat on 2006-05-22
Hello,
    I'm still around thanks.  :)   I am using Puppy Linux 1.09 CE at the moment as I had too many problems trying to install Ubuntu on my SATA drive.  ](*,)  Will try again later though.  :neutral:

---

