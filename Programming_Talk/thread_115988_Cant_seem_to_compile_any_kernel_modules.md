---
title: "Cant seem to compile any kernel modules"
date: 2006-01-11
forum: Programming Talk
---

### Post by zappa86 on 2006-01-11
Hi. I have a few modules that I wish to compile for my kernel but whenver I go to make them it gives me tons of errors:

```
harry@zappa:~/Desktop/misc-modules$ make
make -C /lib/modules/2.6.12-h01/build M=/home/harry/Desktop/misc-modules modulesmake[1]: Entering directory `/usr/src/linux-source-2.6.12'

  WARNING: Symbol version dump /usr/src/linux-source-2.6.12/Module.symvers
           is missing; modules will have no dependencies and modversions.

  CC [M]  /home/harry/Desktop/misc-modules/hello.o
In file included from include/linux/init.h:4,
                 from /home/harry/Desktop/misc-modules/hello.c:4:
include/linux/config.h:4:28: linux/autoconf.h: No such file or directory
In file included from include/linux/module.h:10,
                 from /home/harry/Desktop/misc-modules/hello.c:5:
include/linux/sched.h:4:36: asm/param.h: No such file or directory
In file included from include/linux/posix_types.h:47,
                 from include/linux/types.h:13,

```
thats just the first part of it. It seriousally fills up the virtual terminal so fast and keeps going and going. I have my own custom kernel that I installed (I used the make-kpkg and did that). I have linux-tree installed so I dont know why this happens. I tried to compile another module last week and I got all these errors (it was for a webcam) but I figured that it was just something wrong with the source and I did not do anything about it. But when I tried a few others modules and got all the same errors, i figured I was missing a package or something or need to change some simple variable (not that I know which one needs changing). can anyone help me fix this? thanks

---

