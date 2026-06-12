---
title: "Tons of missing header file errors."
date: 2006-07-27
forum: Programming Talk
---

### Post by funnyfraggle on 2006-07-27
I'm trying to set up a Ubuntu box to write some device drivers. When I try to compile I get several pages of missing file errors like this:

```

include/linux/autoconf.h: No such file or directory
In file included from include/linux/module.h:9,
                 from /home/jay/driver/nothing.c:1:
include/linux/config.h:6:28: error: linux/autoconf.h: No such file or directory
In file included from include/linux/module.h:10,
                 from /home/jay/driver/nothing.c:1:
include/linux/sched.h:4:36: error: asm/param.h: No such file or directory
In file included from include/linux/posix_types.h:47,
                 from include/linux/types.h:14,
                 from include/linux/capability.h:16,
                 from include/linux/sched.h:7,
                 from include/linux/module.h:10,
                 from /home/jay/driver/nothing.c:1:

```

I have installed various kernel header and source packages along with the "build essential" package.

Can anyone tell me what I'm missing here, or perhaps point me to a good how to for setting up this kind of development environment?

--Jay

---

### Post by hod139 on 2006-07-27
Try installing autoconf, automake, and libtool.  Also what commands are you using to generate these errors?

---

### Post by funnyfraggle on 2006-07-27
I have the packages you suggested. The full command is 

```

 make -C /usr/src/linux-source-2.6.15 M=`pwd` modules

```

here is the makefile

```

obj-m := nothing.o

```

---

### Post by ifokkema on 2006-07-27
I don't know exactly where it's looking, but these packages (Breezy) provide an include/linux/autoconf.h:
libc5-altdev: usr/i486-linuxlibc1/include/linux/autoconf.h
libuclibc-dev: usr/i386-uclibc-linux/include/linux/autoconf.h
linux-headers-2.6.12-9: usr/src/linux-headers-2.6.12-9/include/linux/autoconf.h
linux-headers-2.6.12-9-386: usr/src/linux-headers-2.6.12-9-386/include/linux/autoconf.h
linux-headers-2.6.12-9-686: usr/src/linux-headers-2.6.12-9-686/include/linux/autoconf.h
linux-headers-2.6.12-9-686-smp: usr/src/linux-headers-2.6.12-9-686-smp/include/linux/autoconf.h
linux-headers-2.6.12-9-k7: usr/src/linux-headers-2.6.12-9-k7/include/linux/autoconf.h
linux-headers-2.6.12-9-k7-smp: usr/src/linux-headers-2.6.12-9-k7-smp/include/linux/autoconf.h
linux-kernel-headers: usr/include/linux/autoconf.h

HTH

---

### Post by funnyfraggle on 2006-07-27
Thank you. I will try that as soon as I get back to work in the morning.

---

### Post by funnyfraggle on 2006-07-28
Well, I got to compile :D 

I just changed where it was looking for the headers after using "locate" to discover I had like 4 copies of it already.

Thank's to ifokkema and hod139. The forums is what brought me to UBUNTU. My previous excursion to Linux was Fedora and the community there was not even a tenth as cool as you guys.

-- Jay

---

