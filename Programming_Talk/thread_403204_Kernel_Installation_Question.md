---
title: "Kernel Installation Question"
date: 2007-04-06
forum: Programming Talk
---

### Post by twentytortures on 2007-04-06
I hope I'm posting this in the right area.

I decided that I was going to compile a kernel, not for any specific reason, but because it was something new and I wanted to try it.

I was able to configure and 'make' the kernel with no problems. I was able to do a 'make modules_install' as well. The problem comes when I try to install it by doing a 'make install'. I get a message that says:

```
In order to use the new kernel image you have just installed, you
will need to reboot the machine.  First, however, you will need to
either make a bootable floppy diskette, re-run LILO, or have GRUB
installed.

Checking for ELILO...No

GRUB is installed. To automatically switch to new kernels, point your
default entry in menu.lst to /boot/vmlinuz-2.6.20.4

```

Unfortunately I'm too much of a newb to figure out this problem. Do I need to edit 'menu.lst'? If I edit it and change the default entry will that overwrite the kernel I currently have installed? Lastly, where is menu.lst? lol

Thanks!

---

### Post by bruenig on 2007-04-06
The menu.lst is located at /boot/grub/menu.lst.

Doing sudo update-grub should add that kernel assuming you installed it correctly. Or you can always edit it manually.

---

### Post by twentytortures on 2007-04-07
I got it installed, unfortunately I'm having problems with mkinitramfs.
I run
```
sudo mkinitramfs -o initrd.image-2.6.20.4 2.6.20.4
```
and get
```
cp: missing destination file operand after `/tmp/tmp.zEryda5013/sbin/'
Try `cp --help' for more information.
------------------
Error has occured!

```
Any body know what I'm doing wrong?

---

