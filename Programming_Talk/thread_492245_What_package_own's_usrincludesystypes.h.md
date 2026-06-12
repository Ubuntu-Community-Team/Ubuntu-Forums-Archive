---
title: "What package own's /usr/include/sys/types.h?"
date: 2007-07-04
forum: Programming Talk
---

### Post by merkel on 2007-07-04
I'm trying to to run 'make install' for the SNNS neural network package and I get the following error:

$ make install
cd tools/sources && make install-strip
make[1]: Entering directory `/usr/local/src/SNNSv4.2/tools/sources'
make INSTALL_PROGRAM='/usr/bin/install -c  -s' install
make[2]: Entering directory `/usr/local/src/SNNSv4.2/tools/sources'
gcc  -I../.. -I../../kernel/sources  -g -O  -c analyze.c
In file included from ../../config.h:104,
                 from analyze.c:20:
../../kernel/sources/alloca.h:25:23: error: sys/types.h: No such file or directory
analyze.c:21:19: error: stdio.h: No such file or directory
.
.
.

I noticed my Xubuntu does not have a /usr/include/sys/ directory.  My redhat box does have that directory and the types.h file says it is from the GNU C compiler.  I have the GNU C compiler installed on Xubuntu, but there is no types.h file installed with it, according to synaptic.

Anyone know which package /usr/include/sys/types.h comes from?

Thanks,

John

---

### Post by avik on 2007-07-04
build-essential should have it.  Otherwise, maybe glibc has it.

---

### Post by meatpan on 2007-07-04
It looks like the package 'libc6-dev' owns the file.

I ran the following command to verify this:
dpkg -L libc6-dev | grep types.h

---

### Post by merkel on 2007-07-04
Bingo, it's 'libc6-dev', thanks.  That package was installed on my machine, according to Synaptic, but for some reason the entire sys directory was missing.  I did a reinstall and now it's there.

Thanks!

John

---

