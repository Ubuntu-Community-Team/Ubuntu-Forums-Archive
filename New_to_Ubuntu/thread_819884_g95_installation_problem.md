---
title: "g95 installation problem"
date: 2008-06-05
forum: New to Ubuntu
---

### Post by b-laz-io on 2008-06-05
hi
I've just tried to install the fortran compiler, but the installation stops with this written:

.....

g95-install/lib/gcc-lib/i686-suse-linux-gnu/4.0.3/crtendS.o
g95-install/lib/gcc-lib/i686-suse-linux-gnu/4.0.3/crtend.o
g95-install/lib/gcc-lib/i686-suse-linux-gnu/4.0.3/libgcc_s.so
g95-install/lib/gcc-lib/i686-suse-linux-gnu/4.0.3/crtbegin.o
g95-install/lib/gcc-lib/i686-suse-linux-gnu/4.0.3/cc1
blaz@blaz-desktop:~$ ln -s $PWD/g95-install/bin/i686-pc-linux-gnu-g95 /usr/bin/g95
ln: creating symbolic link `/usr/bin/g95' to `/home/blaz/g95-install/bin/i686-pc-linux-gnu-g95': Permission denied


and as I am an absolute beginner on ubuntu, I would be very grateful for some suggestion for solving this problem;)

---

### Post by ZabiGG on 2008-06-05
well... you may need to install as a superuser. Did you try adding sudo before each line?

For info on  Ubuntu and Linux systems, click the "Look here" link in my signature below. It's always good to start with the basics.

Very good luck to you,

Z.

---

