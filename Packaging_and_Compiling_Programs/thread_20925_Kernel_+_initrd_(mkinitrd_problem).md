---
title: "Kernel + initrd (mkinitrd problem?)"
date: 2005-03-19
forum: Packaging and Compiling Programs
---

### Post by d0nk on 2005-03-19
I compile my kernels manually, and always have, and i don't use make-kpkg to do it.  For some reason, after installing Hoary Preview, I cant make an initrd.  

mkinitrd doesn't give any errors, or anything, it just doesnt make an initrd.img.  Here is the command args i use:

root@ubuntu:/boot # mkinitrd -o ./initrd.img-2.6.11 2.6.11

Everything seems to go fine, no errors, but the initrd.img is not made.  I've made initrd images this way for years, and i dont see why its not working for me now.

---

### Post by d0nk on 2005-03-20
[QUOTE=d0nk]I compile my kernels manually, and always have, and i don't use make-kpkg to do it.  For some reason, after installing Hoary Preview, I cant make an initrd.  

mkinitrd doesn't give any errors, or anything, it just doesnt make an initrd.img.  Here is the command args i use:

root@ubuntu:/boot # mkinitrd -o ./initrd.img-2.6.11 2.6.11

Everything seems to go fine, no errors, but the initrd.img is not made.  I've made initrd images this way for years, and i dont see why its not working for me now.[/QUOTE]
 Hm, well, it seems that i dont need an initrd to boot my kernel.  Maybe its because 99.9% of everything is compiled in :p

---

### Post by az on 2005-03-20
Is /etc/mkinitrd setup properly?

What about the -k option.  Is anything left there afterwards if you is it?

---

### Post by wmaddler on 2005-04-04
[QUOTE=d0nk]I compile my kernels manually, and always have, and i don't use make-kpkg to do it.  For some reason, after installing Hoary Preview, I cant make an initrd.  

mkinitrd doesn't give any errors, or anything, it just doesnt make an initrd.img.  Here is the command args i use:

root@ubuntu:/boot # mkinitrd -o ./initrd.img-2.6.11 2.6.11

Everything seems to go fine, no errors, but the initrd.img is not made.  I've made initrd images this way for years, and i dont see why its not working for me now.[/QUOTE]

use the -k option to keep files and the manually launch: mkcramfs /<tmp_data_dir> /boot/initrd_image

that's what mkinitrd was supposed to do...

hope it helps...

---

