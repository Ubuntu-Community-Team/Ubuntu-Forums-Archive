---
title: "compiling linux-2.6.26 kernel"
date: 2009-02-19
forum: Packaging and Compiling Programs
---

### Post by haneef_kernel on 2009-02-19
hi,
when i tried to compile the kernel the following error occurred

haneef@haneef-desktop:~/Desktop/linux-2.6.26$ make menuconfig
  HOSTCC  scripts/basic/fixdep
  HOSTCC  scripts/basic/docproc
  HOSTCC  scripts/kconfig/conf.o
  HOSTCC  scripts/kconfig/kxgettext.o
  HOSTCC  scripts/kconfig/lxdialog/checklist.o
In file included from scripts/kconfig/lxdialog/dialog.h:38,
                 from scripts/kconfig/lxdialog/checklist.c:24:
/usr/local/include/curses.h:96: error: both ‘unsigned’ and ‘_Bool’ in declaration specifiers
make[1]: *** [scripts/kconfig/lxdialog/checklist.o] Error 1
make: *** [menuconfig] Error 2


what can be done for this

---

### Post by eilenbeb on 2009-02-19
Hi.  Not much information to work with, btw.

I'm assuming you haven't modified anything in the scripts/makefiles/codebase, and are (atm) just trying to configure the kernel for build.

Lotsa moving parts when building a kernel.  My first guess is that one of them isn't the right version for the kernel your're building.
Just to be on the safe side, I would go back to the kernel docs and doublecheck the required versions for everything (make, gcc, headers, curses, and so on).

Also, multiple versions of the above can exist simultaneously on the system, and be selected per build session.  For instance, building a particular version of glibc might require a different c compiler than the kernel.
-Somewhere- there are 'switches' for which ones to use (symlinks, environment variables) and I would go back and make sure the environment is set correctly.  (I haven't had to do this yet, so I can't help any further on that one)

Anyways, hope that was helpful in some way, and good luck.
laters,
b

---

