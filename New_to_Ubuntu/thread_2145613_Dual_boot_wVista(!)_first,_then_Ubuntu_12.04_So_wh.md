---
title: "Dual boot w/Vista(!) first, then Ubuntu 12.04: So where is my menu.lst now?"
date: 2013-05-16
forum: New to Ubuntu
---

### Post by RickFAA on 2013-05-16
Hi!
Desktop, new (gift) in 2009, opened last April(2013). Vista(!) 'was' working.  Next set a partition in a unallocated space and put a copy of Ubuntu 12.04 in (not a Live one) . But now Vista is missing somewhere! 
Ubuntu works great, but can't find the "dual-boot" part? Got a Ubuntu Forums archive tutorial(t-371530) to update the Grub file, but my 'menu.lst' is gone.

What to do Now ?

RickO

---

### Post by papibe on 2013-05-16
Hi RickFAA.

I would start using Boot-Repair. Using the installation CD/USB as a live media, you can rescan the bootable partitions and update the grub list. Here's a [tutorial]("https://help.ubuntu.com/community/Boot-Repair").

Let us know how it goes.
Regards.

---

### Post by arpanaut on 2013-05-16
If the tutorial you used was referring to menu.list then the tut. was out of date for 12.04
as in grub2 menu.list is not used, can you provide a link to the tutorial you used.

If you are logged in to Ubuntu please provide the output from a terminal (ctrl+alt+t)of:
(copy and paste this into terminal, provide user password, and copy and paste results back here.)
```
sudo fdisk -lu
```

You could also try in a terminal:```
sudo update-grub
```
which will try again to detect the OS's on your system and put Windows in the boot screen if it is detected.

Hopefully you did not overwrite your windows install but the first command provided should provide some clues to that.

Edit: Or do what papibe suggested...):P

---

### Post by RickFAA on 2013-05-16
Thank you for the quick reply.......here is one or two back......
 
The DIRECT LINK tutorial(2007!) is: 
([http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first))

Is my GRUB: menu.lst or menu.list?
Wow - there is a grub2.......?

And some other stuff.......

uncle-Inspiron-537s:/home$ sudo fdisk -lu

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd93a2314

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       80324       40131   de  Dell Utility
/dev/sda2           81920    30801919    15360000    7  HPFS/NTFS/exFAT
/dev/sda3   *    30801920   354988711   162093396    7  HPFS/NTFS/exFAT
/dev/sda4       354992126   625141759   135074817    5  Extended
/dev/sda5       354992128   600752127   122880000   83  Linux
/dev/sda6       600754176   616755199     8000512   83  Linux
/dev/sda7       616757248   625141759     4192256   82  Linux swap / Solaris

uncle-Inspiron-537s:/home$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.5.0-28-generic
Found initrd image: /boot/initrd.img-3.5.0-28-generic
Found linux image: /boot/vmlinuz-3.5.0-23-generic
Found initrd image: /boot/initrd.img-3.5.0-23-generic
Found linux image: /boot/vmlinuz-3.2.0-41-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-41-generic-pae
Found memtest86+ image: /boot/memtest86+.bin
Found Windows Vista (loader) on /dev/sda3
done

I was trying to get a copy of "ppa:yannubuntu/boot-repair", but  my sudo said:
add-apt: command not found!

This is FUN!
RickO

---

### Post by arpanaut on 2013-05-16
Very good, now you should be able to boot windows by selecting the last item on the list at the boot screen (arrow down, hit enter)
then when you want Ubuntu again, reboot & just let it go 10 sec and you have dual boot. (or hit enter to go to Ubuntu)

Yeah, this is fun, lotsa stuff to learn, You should be cooking with gas now... LOL

Yikes, 2007, you have to be careful about what tutorials you follow, things change pretty fast in the Linux world.

---

