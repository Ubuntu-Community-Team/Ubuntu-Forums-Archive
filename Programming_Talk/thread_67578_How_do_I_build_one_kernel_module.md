---
title: "How do I build one kernel module?"
date: 2005-09-20
forum: Programming Talk
---

### Post by chaumurky on 2005-09-20
I have to apply a very small patch to a single module to get my Fusion HTDV T1 to tune properly. Is there any way I can re-compile this one module instead of building them all?

EDIT: Nice,my 100th post!  :grin:

---

### Post by jerome bettis on 2005-09-21
[QUOTE=chaumurky]I have to apply a very small patch to a single module to get my Fusion HTDV T1 to tune properly. Is there any way I can re-compile this one module instead of building them all?

EDIT: Nice,my 100th post!  :grin:[/QUOTE]
 absolutely.  if you have the driver it should have a readme or install file you can read.  if not you can probably just type
patch -p1 < filename (to apply patch)
./configure
make
make install  (as root)

to install it for the currently running kernel. you'll need to apt-get the kernel-headers package along with build-essential if you don't have those already. then you have to edit a file called /etc/modules (i think) and just add the module name in there so it's loaded at boot.

  if what i'm saying makes no sense ... search here and google for compiling kernel modules and such,

---

### Post by chaumurky on 2005-09-21
I've actually done the patch and a full kernel rebuild a little while back. With the Breezy preview release I decided to to a re-install but I forgot to backup the patched module. The file to be patched is dvb-pll.c and the folder it resides in (/usr/src/linux/drivers/media/dvb/frontends/) has no .configure script so I don't think it's as straightforward as that. If I did a 'make modules' that would speed things up a little but really just the one module would be preferable. I'll keep looking and post back if I work something out.

---

