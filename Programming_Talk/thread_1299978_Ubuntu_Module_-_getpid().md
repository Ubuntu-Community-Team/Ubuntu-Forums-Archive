---
title: "Ubuntu Module - getpid()"
date: 2009-10-24
forum: Programming Talk
---

### Post by hutcro on 2009-10-24
Hello all,

I am attempting to write a basic module for ubuntu 9.04. My difficulty is trying to call the getpid function when the module is loaded.  From what I gather the sys/types.h contains the variable type pid_t and unistd.h contains the declaration for getpid(void).

However, when compiling my code, I keep getting: "error: implicit declaration of function 'getpid'".  The module code works fine if I exclude using the getpid function.

I assume that this is because the correct header containing the declaration for getpid is not loaded.  The code for the module is below.  Is there something I am overlooking or are there any good resources that discuss this? (I haven't been able to find much by way of search engines).  Any help/advice is appreciated.  Thanks!

```

#include <linux/init.h>
#include <linux/module.h>
#include <linux/kernel.h>

#include <asm/types.h>
#include <linux/unistd.h>


static int hello_init(void)
{
     pid_t pid = getpid();  /*errors on the getpid function */
     printk(KERN_INFO " module loaded %d\n", pid);
     return 0;
}

static void hello_exit(void)
{
     printk(KERN_INFO " module unloaded\n");
}

module_init(hello_init);
module_exit(hello_exit);

MODULE_LICENSE("GPL");
MODULE_AUTHOR("asdf");

```

---

### Post by Zugzwang on 2009-10-24
"Grep" is your friend.

```

user@user-laptop:/usr/src/linux-headers-2.6.28-13-generic$ grep -Hrni getpid *
arch/cris/include/asm/unistd.h:28:#define __NR_getpid            20
arch/alpha/include/asm/unistd.h:244:#define __IGNORE_getpid
arch/powerpc/include/asm/systbl.h:26:SYSCALL_SPU(getpid)
arch/powerpc/include/asm/unistd.h:33:#define __NR_getpid                 20
arch/parisc/include/asm/unistd.h:31:#define __NR_HPUX_getpid                 20
arch/parisc/include/asm/unistd.h:513:#define __NR_getpid              (__NR_Linux + 20)
arch/blackfin/include/asm/unistd.h:26:#define __NR_getpid                20
arch/um/include/shared/os.h:182:extern int os_getpid(void);
arch/ia64/include/asm/perfmon_default_smpl.h:72:        int             tgid;                   /* thread group id (for NPTL, this is getpid()) */
arch/ia64/include/asm/unistd.h:32:#define __NR_getpid                   1041
arch/x86/include/asm/unistd_64.h:97:#define __NR_getpid                         39
arch/x86/include/asm/unistd_64.h:98:__SYSCALL(__NR_getpid, sys_getpid)
arch/x86/include/asm/unistd_32.h:28:#define __NR_getpid          20
arch/avr32/include/asm/unistd.h:35:#define __NR_getpid           20
arch/sparc/include/asm/unistd_64.h:38:#define __NR_getpid              20 /* Common                                      */
arch/sparc/include/asm/unistd_32.h:38:#define __NR_getpid              20 /* Common                                      */
arch/s390/include/asm/unistd.h:31:#define __NR_getpid              20
arch/sh/include/asm/unistd_64.h:37:#define __NR_getpid           20
arch/sh/include/asm/unistd_32.h:32:#define __NR_getpid           20
arch/mips/include/asm/unistd.h:43:#define __NR_getpid                   (__NR_Linux +  20)
arch/mips/include/asm/unistd.h:408:#define __NR_getpid                  (__NR_Linux +  38)
arch/mips/include/asm/unistd.h:714:#define __NR_getpid                  (__NR_Linux +  38)
arch/m68knommu/include/asm/unistd.h:28:#define __NR_getpid               20
arch/arm/include/asm/unistd.h:48:#define __NR_getpid                    (__NR_SYSCALL_BASE+ 20)
arch/h8300/include/asm/unistd.h:28:#define __NR_getpid           20
include/asm-mn10300/unistd.h:34:#define __NR_getpid              20
include/asm-xtensa/unistd.h:280:#define __NR_getpid                             120
include/asm-xtensa/unistd.h:281:__SYSCALL(120, sys_getpid, 0)
include/asm-xtensa/platform-iss/simcall.h:39:#define SYS_getpid 20
include/asm-m32r/unistd.h:28:#define __NR_getpid                 20
include/asm-m68k/unistd.h:27:#define __NR_getpid                 20
include/asm-frv/unistd.h:28:#define __NR_getpid          20
include/linux/sem.h:10:#define GETPID  11       /* get sempid */
include/linux/syscalls.h:150:asmlinkage long sys_getpid(void);
scripts/kconfig/confdata.c:430:         sprintf(tmpname, "%s.tmpconfig.%d", dirname, (int)getpid());

```

Looks like you need to use the "sys_getpid" function instead, which is in "linux/syscalls.h".

---

### Post by lensman3 on 2009-10-24
Change the line: #include <linux/unistd.h> 


to

#include <unistd.h>


getpid() lives int that include file located at "/usr/include/unistd.h"

getpid() returns a value of type pid_t which is probably typedefed to an integer.  pid_t is found in the include file 

#include <sys/types.h>

You are using includes from <linux/xxxxx.h>.   I think the "linux" include directory is used by other higher level includes to finally point to the Linux gcc compiler library.  It is very Linux specific for the gcc and probably not portable.

The "man" pages, short for manual, are found in the text window.  If you do a "man getpid" you will see the complete write up for get-process ID.   At the top of the man page is the required include files.  The number in parens in getpid(2) points to which library subdivision the function lives  in.  Occasionally, the man pages will bring up the wrong function, so typing, "man 2 getpid" will specifically retrieve the  correct description.

The other helpful command is "man -k xxxx" where xxxx is an appropriate word that you are trying to figure out.  If you do "man -k process", get process ID is one of the very man lines returned.  It is best to pipe this output through "more".  The sub-library, the number in paren, is helpful in this case where the same command can be described in two ore more places.

---

### Post by Can+~ on 2009-10-25
To have access to the system call and libraries man pages, you need the doc:

```
sudo apt-get install manpages-dev
```

---

### Post by hutcro on 2009-10-26
I finally figured out that since it's a module, you can use: current->pid.  Thanks for the tips, they helped get me to the solution.

Thanks!

---

