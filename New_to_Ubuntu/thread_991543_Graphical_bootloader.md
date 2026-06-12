---
title: "Graphical bootloader"
date: 2008-11-23
forum: New to Ubuntu
---

### Post by Tsurugi13 on 2008-11-23
A while ago I was forced to give up using Ubuntu when my computer died. :( I'd like to get back into it, as it seems most programming languages work best in UNIX. My biggest complaint with using it before was GRUB. I'd like to find a bootloader with a nice GUI or at least one that doesn't have defaults set, as I'll be using XP too, if only for compatibility reasons. I've looked around some but have been unable to find anything. Does anyone know where I can find something like this?

---

### Post by DGortze380 on 2008-11-23
[http://gag.sourceforge.net/pics.html](http://gag.sourceforge.net/pics.html)

---

### Post by Locutus_of_Borg on 2008-11-23
why do you need graphics loaded prior to even entering an operating system?
and grub can be made to look pretty: [link]("http://blog.sckyzo.com/wp-content/grubgfxexemple.jpg")

---

### Post by Tsurugi13 on 2008-11-23
> **Locutus_of_Borg said:**
> why do you need graphics loaded prior to even entering an operating system?
and grub can be made to look pretty: [link]("http://blog.sckyzo.com/wp-content/grubgfxexemple.jpg")

That's basically all I want to do :| Can GRUB also be set to NOT have a default boot OS? I'd rather just have to pick every time I boot it.

---

### Post by Locutus_of_Borg on 2008-11-23
yes, grub will just show a list of OS's

you can choose their order, you can choose to set a timer to select one after # seconds, or to just wait indefinitely for your selection,

Everything is in grub.conf or menu.lst located in /boot/grub

---

### Post by handydan918 on 2008-11-23
> **Locutus_of_Borg said:**
> yes, grub will just show a list of OS's

you can choose their order, you can choose to set a timer to select one after # seconds, or to just wait indefinitely for your selection,

Everything is in grub.conf or menu.lst located in /boot/grub

+1! 
Like everything else in Linux, GRUB is nearly infinitely configurable. 
And THAT is the strength, and weakness, of Linux.


](*,)

---

### Post by jimreynold2nd on 2008-11-23
Look at my grub screenshot & config. And that's without GrUBfx.
```


default=saved
timeout=5
splashimage=(hd0,4)/grub/duyblack.xpm.gz
password --md5 --deleted, although it is hashed--

title Ubuntu 8.04.1 GNOME
	root (hd0,7)
	kernel /boot/vmlinuz-2.6.24-21-generic root=/dev/sda8 ro quiet splash
	initrd /boot/initrd.img-2.6.24-21-generic
	savedefault
	quiet

title Ubuntu 8.10 KDE4
	root (hd0,8)
#	kernel /boot/vmlinuz-2.6.27-7-generic root=/dev/sda9 ro quiet splash
	kernel /boot/vmlinuz-2.6.27-7-generic root=/dev/sda9 ro vga=0x317
	initrd /boot/initrd.img-2.6.27-7-generic
	savedefault
	quiet

title XP SP3
	root (hd0,1)
	makeactive
	chainloader +1
	savedefault
	quiet

title Vista SP1
	root (hd0,0)
	makeactive
	chainloader +1
	savedefault
	quiet

title Mac OSX Leopard
	root (hd0,2)
	makeactive
	chainloader +1
	savedefault
	quiet

title -------------------------------------------
	root (hd0,4)
	quiet

title Backtrack 3 (Live)
	lock
	root (hd0,5)
	kernel /boot/vmlinuz vga=791 ramdisk_size=9999 root=/dev/ram0 rw chexpand=160 autoexec=xconf;kdm
	initrd /boot/initrd.gz

title Helix 1.9 (Live)
	lock
	#configfile (hd0,6)/boot/grub/menu.lst
	root (hd0,6)
	kernel /boot/vmlinuz vga=791 ramdisk_size=100000 init=/etc/init lang=us apm=power-off nomce unionfs quiet
	initrd /boot/miniroot.gz

title SysRescue CD (Live)
	lock
	root (hd0,4)
	kernel /sysrcd/rescuecd
	initrd /sysrcd/initram.igz

title Paragon Partition Manager 9
	lock
	root (hd0,4)
	kernel /paragon/vmlinuzp vga=791 language=it_IT.UTF-8 medialable=PARAGON
	initrd /paragon/initrd.gz

title -------------------------------------------
	root (hd0,4)
	quiet

title Boot from CD
	lock
	root (hd0,4)
	kernel /cdmenu/memdisk.bin
	initrd /cdmenu/sbootmgr.dsk

```

---

### Post by Tsurugi13 on 2008-11-23
That settles it then. I'm going to give it a go. Gonna back up first though, last time I wiped windows by mistake. :|

---

