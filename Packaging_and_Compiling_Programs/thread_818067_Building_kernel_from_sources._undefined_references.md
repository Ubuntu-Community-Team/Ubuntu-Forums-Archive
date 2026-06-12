---
title: "Building kernel from sources. undefined references"
date: 2008-06-04
forum: Packaging and Compiling Programs
---

### Post by stari4ek on 2008-06-04
Following [steps from official document (url)]("https://help.ubuntu.com/community/Kernel/Compile") I've tried to build binary-generic kernel with default configs.
```
AUTOBUILD=1 NOEXTRAS=1 fakeroot debian/rules binary-generic
```

and got errors:
```
  LD      .tmp_vmlinux1
kernel/built-in.o: In function `timespec_add_ns':
/home/astar/bldtmp/linux-2.6.24/include/linux/time.h:177: undefined reference to `__umoddi3'
/home/astar/bldtmp/linux-2.6.24/include/linux/time.h:177: undefined reference to `__udivdi3'
kernel/built-in.o: In function `timespec_add_ns':
/home/astar/bldtmp/linux-2.6.24/kernel/time/timekeeping.c:127: undefined reference to `__udivdi3'
/home/astar/bldtmp/linux-2.6.24/kernel/time/timekeeping.c:127: undefined reference to `__umoddi3'
kernel/built-in.o: In function `timespec_add_ns':
/home/astar/bldtmp/linux-2.6.24/include/linux/time.h:177: undefined reference to `__umoddi3'
/home/astar/bldtmp/linux-2.6.24/include/linux/time.h:177: undefined reference to `__udivdi3'
/home/astar/bldtmp/linux-2.6.24/include/linux/time.h:177: undefined reference to `__umoddi3'
/home/astar/bldtmp/linux-2.6.24/include/linux/time.h:177: undefined reference to `__udivdi3'
/home/astar/bldtmp/linux-2.6.24/include/linux/time.h:177: undefined reference to `__umoddi3'
```

As i can see __udivdi3/__umoddi3 exist only in some of non-x86 arches.

Is that guide still valid?
Should I prefer building kernel from kernel-source package?


package: linux_2.6.24-18.32
gcc: gcc version 4.3.0 (Ubuntu 4.3.0-1ubuntu1)

---

### Post by jtrindle on 2008-06-04
It looks like this thread is related:

[http://bbs.archlinux.org/viewtopic.php?id=45882](http://bbs.archlinux.org/viewtopic.php?id=45882)

Summary: kernel 2.6.24 source isn't necessarily set up to compile under gcc 4.3 by default.

---

