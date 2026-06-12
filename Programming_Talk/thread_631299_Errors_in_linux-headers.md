---
title: "Errors in linux-headers"
date: 2007-12-04
forum: Programming Talk
---

### Post by bbackx on 2007-12-04
Hi,

I'm currently working on the development of a linux-driver for a firewire-device and I'm having some problems.
There is some existing code, but it's outdated (coded for kernel 2.4 or early 2.6).
Now, I'm trying to compile the code to see which function-calls need to be modified. However, I'm not only getting errors in the existing code, but also in the kernel-source I installed using the ubuntu-repositories.

I'm compiling using the following command:
cc -I /usr/src/linux-source-2.6.22/include -I /usr/src/linux-source-2.6.22/drivers/ieee1394 device.c

I know using the linux-headers is recommended, but than I'm unable to found the headers in /drivers/ieee1394 (empty folder).
I also tried compiling using generic linux-source from kernel.org, but the problems remain.

A small part of the errors I got:
```
In file included from /usr/src/linux-headers-2.6.22-14/include/asm/bitops.h:9,

                 from /usr/src/linux-headers-2.6.22-14/include/linux/bitops.h:9,

                 from /usr/src/linux-headers-2.6.22-14/include/linux/thread_info.h:20,

                 from /usr/src/linux-headers-2.6.22-14/include/linux/preempt.h:9,

                 from /usr/src/linux-headers-2.6.22-14/include/linux/spinlock.h:49,

                 from /usr/src/linux-headers-2.6.22-14/include/linux/module.h:9,

                 from device.c:14:

/usr/src/linux-headers-2.6.22-14/include/asm/alternative.h:9: error: expected specifier-qualifier-list before ‘u8’

In file included from /usr/src/linux-headers-2.6.22-14/include/linux/bitops.h:9,

                 from /usr/src/linux-headers-2.6.22-14/include/linux/thread_info.h:20,

                 from /usr/src/linux-headers-2.6.22-14/include/linux/preempt.h:9,

                 from /usr/src/linux-headers-2.6.22-14/include/linux/spinlock.h:49,

                 from /usr/src/linux-headers-2.6.22-14/include/linux/module.h:9,

                 from device.c:14:

/usr/src/linux-headers-2.6.22-14/include/asm/bitops.h:244: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘int’

In file included from /usr/src/linux-headers-2.6.22-14/include/asm/system.h:7,

                 from /usr/src/linux-headers-2.6.22-14/include/linux/spinlock.h:57,

                 from /usr/src/linux-headers-2.6.22-14/include/linux/module.h:9,

                 from device.c:14:

/usr/src/linux-headers-2.6.22-14/include/asm/cmpxchg.h:213: error: expected declaration specifiers or ‘...’ before ‘u8’

/usr/src/linux-headers-2.6.22-14/include/asm/cmpxchg.h:213: error: expected declaration specifiers or ‘...’ before ‘u8’

/usr/src/linux-headers-2.6.22-14/include/asm/cmpxchg.h:214: error: expected declaration specifiers or ‘...’ before ‘u16’

/usr/src/linux-headers-2.6.22-14/include/asm/cmpxchg.h:214: error: expected declaration specifiers or ‘...’ before ‘u16’

/usr/src/linux-headers-2.6.22-14/include/asm/cmpxchg.h:215: error: expected declaration specifiers or ‘...’ before ‘u32’

/usr/src/linux-headers-2.6.22-14/include/asm/cmpxchg.h:215: error: expected declaration specifiers or ‘...’ before ‘u32’

```

Hopefully, someone can help me out...

---

### Post by geirha on 2007-12-04
is asm pointing to the correct architecture?
```
readlink -f /usr/src/linux-headers-2.6.22-14/include/asm
```

---

### Post by bbackx on 2007-12-04
I think so:
```
/usr/src/linux-headers-2.6.22-14/include/asm-i386
```

(the pc is based on an AMD Athlon XP 2500+)

---

