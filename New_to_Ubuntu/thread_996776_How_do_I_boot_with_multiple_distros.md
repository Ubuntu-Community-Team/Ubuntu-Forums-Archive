---
title: "How do I boot with multiple distros?"
date: 2008-11-29
forum: New to Ubuntu
---

### Post by gabriella on 2008-11-29
Right now I dual boot with Win XP and Ubuntu. By default it goes into Hardy.
But on my desktop I have oodles of unused HD space. I want to put another Linux distro on to try for a while. However, I still want the default to be Hardy and if I want to play with the other I can select it just like I do for XP.

BUt how should I do that? From what I gather if I just install the new distro it can take over the boot process. It's something (I think?) about having the new distro install their Grub to the boot sector of its own partition and not the MBR. But how exactly do I do that. Please be Specific :confused::confused:

Many thanks!

---

### Post by __Ryan__ on 2008-11-29
You can go ahead and install the other distribution.  I't will overwrite your MBR and install its own boot loader. 

You can either keep this new boot loader and edit the /boot/grub/menu.lst so that Ubuntu is still the default OS, or you can go back into Ubuntu and reinstall GRUB to the MBR which is not too difficult.

In either solution you will have to add the entry for the other installation.

Good luck

---

### Post by davidbilla on 2008-11-29
One way is to choose not to install the bootloader while installing the new distribution. Most popular distros have this option. Either there will be a button that says 'Bootloader options' or something like that or maybe the bootloader options are in 'Advanced' options. It won't be difficult to find out.

After installation you can add an entry to the new distro in your ubuntu's '/boot/grub/menu.lst'.

A typical entry will look like... well, you'll know when you take a look at 'menu.lst'!

---

### Post by philinux on 2008-11-29
Read through my old thread. 
[http://ubuntuforums.org/showthread.php?t=861205&highlight=grub](http://ubuntuforums.org/showthread.php?t=861205&highlight=grub)

And in particular this tutorial.
[http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817)

I'm only dual booting but the principal is the same.

```
This is my menu.lst from disk 1.
title        Ubuntu 8.10, kernel 2.6.27-7-generic
uuid        522831b0-eca2-4c64-bcca-9536056b57be
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=522831b0-eca2-4c64-bcca-9536056b57be ro splash vga=791 
initrd        /boot/initrd.img-2.6.27-7-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid        522831b0-eca2-4c64-bcca-9536056b57be
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=522831b0-eca2-4c64-bcca-9536056b57be ro  single
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 8.10, memtest86+
uuid        522831b0-eca2-4c64-bcca-9536056b57be
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#
title        Whatever's on SDB
configfile   (hd1,0)/boot/grub/menu.lst
```

---

