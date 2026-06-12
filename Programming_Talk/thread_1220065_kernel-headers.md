---
title: "kernel-headers"
date: 2009-07-22
forum: Programming Talk
---

### Post by Tobi-fp on 2009-07-22
Hey..
I wanna start programming kernel modules, and therefore i got the kernel-source of off kernel.org

i made a file 
nothing.o:
---------------------------------------------------------------
#include <linux/module.h>

static int __init hello_world( void )
{
  printk( "hello world!\n" );
  return 0;
}

static void __exit goodbye_world( void )
{
  printk( "goodbye world!\n" );
}

module_init( hello_world );
module_exit( goodbye_world );  

-------------------------------------------------------------


and a makefile:
makefile:

-----------------------------------------------------------
obj-m := nothing.o
-----------------------------------------------------------

the result in terminal when i do #sudo make -C /usr/src/linux-source-2.6.28 M=pwd modules

-------------------------------------------------------------
make: Entering directory `/usr/src/linux-source-2.6.28'

  ERROR: Kernel configuration is invalid.
         include/linux/autoconf.h or include/config/auto.conf are missing.
         Run 'make oldconfig && make prepare' on kernel src to fix it.


  WARNING: Symbol version dump /usr/src/linux-source-2.6.28/Module.symvers
           is missing; modules will have no dependencies and modversions.

scripts/Makefile.build:41: /usr/src/linux-source-2.6.28/pwd/Makefile: No such file or directory
make[1]: *** No rule to make target `/usr/src/linux-source-2.6.28/pwd/Makefile'.  Stop.
make: *** [_module_pwd] Error 2
make: Leaving directory `/usr/src/linux-source-2.6.28'

-----------------------------------------------------------------

what am i doing wrong?
i couldnt sudo apt-get install kernel-headers??

---

### Post by soltanis on 2009-07-22
The correct package is linux-kernel-headers and should autoconfigure itself correctly.

---

### Post by dwhitney67 on 2009-07-22
> **Tobi-fp said:**
> ...

the result in terminal when i do #sudo make -C /usr/src/linux-source-2.6.28 M=pwd modules

...


Hopefully by now you have the kernel header files (also known as the kernel source), as indicated by soltanis.

One thing that irks me is that some documentation/tutorials specify the use of /usr/src/linux-blah-blah-blah as the location of the kernel source code.  This practice is wrong; the correct location is /lib/modules/`uname -r`/build.

If this path is equivalent to your /usr/src/linux-blah-blah-blah, then this is merely coincidental.  The path you are using is not applicable to all Linux systems, and thus should be avoided.

---

