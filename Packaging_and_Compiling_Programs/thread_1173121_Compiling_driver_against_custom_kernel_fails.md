---
title: "Compiling driver against custom kernel fails"
date: 2009-05-29
forum: Packaging and Compiling Programs
---

### Post by SteelWo1f on 2009-05-29
Hi

I made a custom kernel using fakeroot and make-kpkg and called it 2.6.24-24-racetrack. Now I am trying to compile a driver against the new kernel that normally compiles fine. I get the following errors when I try to compile

make[1]: Entering directory `/usr/src/linux-headers-2.6.24-24-racetrack'
/usr/src/linux-headers-2.6.24-24-racetrack/arch/x86/Makefile:15: /usr/src/linux-headers-2.6.24-24-racetrack/arch/x86/Makefile_32: No such file or directory

and

In file included from include/linux/posix_types.h:47,
                 from include/linux/types.h:11,
                 from include/linux/kernel.h:13,
                 from /root/bp_ctl-5.0.28/bp_mod.c:20:
/usr/lib/gcc/i486-linux-gnu/4.2.4/include/asm/posix_types.h:13:22: error: features.h: No such file or directory

There is only the src/linux-headers-2.6.24-24-racetrack/Makefile. All the other Makefiles that are normally there are missing. How do I make them?

And for the next error, include/asm is a symlink to asm-i386. But that file doesn't exist. If I symlink it instead to x86 it seems to clear up some errors, but I shouldn't have to do that.

I am so lost right now!!! Can anyone please help me.

Thanks

---

