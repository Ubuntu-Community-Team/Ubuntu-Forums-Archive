---
title: "gcc -m32 not working"
date: 2011-06-06
forum: Packaging and Compiling Programs
---

### Post by Donenzone on 2011-06-06
Hi,

Whenever I try to execute an assembly program with the following command
gcc -m32 -o hello hello.s

The following happens:
/usr/bin/ld: skipping incompatible /usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2/libgcc.a when searching for -lgcc
/usr/bin/ld: cannot find -lgcc
/usr/bin/ld: skipping incompatible /usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2/libgcc_s.so when searching for -lgcc_s
/usr/bin/ld: cannot find -lgcc_s
/usr/bin/ld: skipping incompatible /usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2/../../../libc.so when searching for -lc
/usr/bin/ld: skipping incompatible /usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2/../../../libc.a when searching for -lc
/usr/bin/ld: skipping incompatible /usr/lib/x86_64-linux-gnu/libc.so when searching for -lc
/usr/bin/ld: skipping incompatible /usr/lib/x86_64-linux-gnu/libc.a when searching for -lc
/usr/bin/ld: cannot find -lc
/usr/bin/ld: skipping incompatible /usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2/libgcc.a when searching for -lgcc
/usr/bin/ld: cannot find -lgcc
/usr/bin/ld: skipping incompatible /usr/lib/x86_64-linux-gnu/gcc/x86_64-linux-gnu/4.5.2/libgcc_s.so when searching for -lgcc_s
/usr/bin/ld: cannot find -lgcc_s
collect2: ld returned 1 exit status

I do not understand what I am doing wrong. Does anyone have any idea on why this is not working?

I am running Natty 64 bit.

Thanks in advance!

---

### Post by MadCow108 on 2011-06-07
do you have gcc-multilib installed?

---

### Post by Donenzone on 2011-06-07
> **MadCow108 said:**
> do you have gcc-multilib installed?

Thank you. After installing that package, it all works again.

---

