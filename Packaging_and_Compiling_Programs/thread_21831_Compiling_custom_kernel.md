---
title: "Compiling custom kernel"
date: 2005-03-24
forum: Packaging and Compiling Programs
---

### Post by matthis on 2005-03-24
After following the instructions in the Wiki, I have managed to build a custom kernel (i think...). However, when trying to install it, I get the following errors:

$sudo dpkg -i my_custom_kernel.deb

Setting up kernel-image-2.6.8.1.1908 (10.00.Custom) ...
/usr/sbin/mkinitrd: add_modules_dep_2_5: modprobe failed
FATAL: Module sg not found.
FATAL: Module sbp2 not found.
FATAL: Module sd_mod not found.
Failed to create initrd image.
dpkg: error processing kernel-image-2.6.8.1.1908 (--install):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 kernel-image-2.6.8.1.1908

Does anyone know how I should proceed?
Thanks

---

### Post by az on 2005-03-24
It would seem that you are telling mkinitrd to include some modules into the intrd that you did not build.  Look in /etc/mkinitrd

---

### Post by matthis on 2005-03-24
hmmm... actually this is the first time I do this so I'm not sure what I sould check, but...
In the /etc/mkinitdr folder, I have:

mkinitdr.conf:
MODULES=all
DELAY=0
ROOT=probe
UMASK=022
MKIMAGE='mkcramfs %s %s > /dev/null'
BUSYBOX=no
PKGSCRIPTS=yes
INITRD_LD_LIBRARY_PATH=$LD_LIBRARY_PATH

and also /etc/mkinitrd/modules, which has nothing inside. (the root fs is on a firewire drive, should I put that there?)

Any clues to what caused the error at kernel installation?
Thanks for any help

---

### Post by Vrok on 2005-03-24
[QUOTE=matthis]
Any clues to what caused the error at kernel installation?
Thanks for any help[/QUOTE]
My clue is that it has failed to create an initrd image ;)
Well, as azzz said, you probably haven't compiled those three modules (mkinitrd has detected that you use them, thus it has tried to include them into initrd). Just make a step back and reconfigure your kernel.

---

### Post by az on 2005-03-24
Also, make sure that you have enabled cramfs since debian intrd are on cramfs.

---

### Post by matthis on 2005-03-25
umm... sorry for the newbie question, but how do I know if cramfs is enabled? I couldn't find it in the kernel options in the "menuconfig"...

---

### Post by maqi on 2005-04-05
If you're using make menuconfig then you will find it under "File Systems ---> Miscellaneous File Systems"

maqi

---

