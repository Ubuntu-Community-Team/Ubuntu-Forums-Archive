---
title: "[SOLVED] unable compiling hello.c module"
date: 2008-09-29
forum: Programming Talk
---

### Post by kcode on 2008-09-29
Thats hello.c code, which i compiled(as root) using the following command
gcc -c -Wall -D_KERNEL_ -DMODULE -I /usr/src/linux-headers-2.6.24-18/include hello.c, 

define MODULE
#include <linux/module.h>

int init_module (void)
{
	printk("Hello kernel\n");
	return 0;
}

void cleanup_module (void)
{
	printk("goodbye kernel\n");
}

with error:
hello.c:1: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before numeric constant
In file included from /usr/src/linux-headers-2.6.24-18/include/linux/module.h:9,
                 from hello.c:2:
/usr/src/linux-headers-2.6.24-18/include/linux/list.h:995:2: warning: #warning "don't include kernel headers in userspace"
In file included from /usr/src/linux-headers-2.6.24-18/include/linux/module.h:12,
                 from hello.c:2:
/usr/src/linux-headers-2.6.24-18/include/linux/cache.h:5:23: error: asm/cache.h: No such file or directory
In file included from /usr/src/linux-headers-2.6.24-18/include/linux/module.h:14,
                 from hello.c:2:
/usr/src/linux-headers-2.6.24-18/include/linux/elf.h:396: error: expected declaration specifiers or ‘...’ before ‘loff_t’
In file included from /usr/src/linux-headers-2.6.24-18/include/linux/module.h:18,
                 from hello.c:2:
/usr/src/linux-headers-2.6.24-18/include/linux/marker.h:103: error: expected declaration specifiers or ‘...’ before numeric constant
/usr/src/linux-headers-2.6.24-18/include/linux/marker.h:103: error: expected declaration specifiers or ‘...’ before numeric constant
/usr/src/linux-headers-2.6.24-18/include/linux/marker.h: In function ‘__printf’:
/usr/src/linux-headers-2.6.24-18/include/linux/marker.h:103: error: expected declaration specifiers before ‘__mark_check_format’
/usr/src/linux-headers-2.6.24-18/include/linux/marker.h:107: error: storage class specified for parameter ‘__mark_empty_function’
/usr/src/linux-headers-2.6.24-18/include/linux/marker.h:114: error: storage class specified for parameter ‘marker_probe_register’
/usr/src/linux-headers-2.6.24-18/include/linux/marker.h:119: error: storage class specified for parameter ‘marker_probe_unregister’
/usr/src/linux-headers-2.6.24-18/include/linux/marker.h:123: error: storage class specified for parameter ‘marker_probe_unregister_private_data’
/usr/src/linux-headers-2.6.24-18/include/linux/marker.h:125: error: storage class specified for parameter ‘marker_arm’
/usr/src/linux-headers-2.6.24-18/include/linux/marker.h:126: error: storage class specified for parameter ‘marker_disarm’
/usr/src/linux-headers-2.6.24-18/include/linux/marker.h:127: error: storage class specified for parameter ‘marker_get_private_data’
In file included from hello.c:2:
/usr/src/linux-headers-2.6.24-18/include/linux/module.h:19:23: error: asm/local.h: No such file or directory
/usr/src/linux-headers-2.6.24-18/include/linux/module.h:21:24: error: asm/module.h: No such file or directory
In file included from hello.c:2:
/usr/src/linux-headers-2.6.24-18/include/linux/module.h:37: warning: empty declaration
/usr/src/linux-headers-2.6.24-18/include/linux/module.h:43: warning: empty declaration
/usr/src/linux-headers-2.6.24-18/include/linux/module.h:45: warning: empty declaration
/usr/src/linux-headers-2.6.24-18/include/linux/module.h:48: error: field ‘attr’ has incomplete type
/usr/src/linux-headers-2.6.24-18/include/linux/module.h:49: error: expected specifier-qualifier-list before ‘ssize_t’
/usr/src/linux-headers-2.6.24-18/include/linux/module.h:55: warning: empty declaration
/usr/src/linux-headers-2.6.24-18/include/linux/module.h:59: error: field ‘kobj’ has incomplete type
/usr/src/linux-headers-2.6.24-18/include/linux/module.h:62: warning: empty declaration
/usr/src/linux-headers-2.6.24-18/include/linux/module.h:65: error: storage class specified for parameter ‘init_module’
/usr/src/linux-headers-2.6.24-18/include/linux/module.h:66: error: storage class specified for parameter ‘cleanup_module’
/usr/src/linux-headers-2.6.24-18/include/linux/module.h:69: warning: empty declaration
/usr/src/linux-headers-2.6.24-18/include/linux/module.h:84: error: storage class specified for parameter ‘__this_module’
/usr/src/linux-headers-2.6.24-18/include/linux/module.h:165: warning: empty declaration
/usr/src/linux-headers-2.6.24-18/include/linux/module.h:477: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/linux-headers-2.6.24-18/include/linux/module.h:483: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/linux-headers-2.6.24-18/include/linux/module.h:489: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/linux-headers-2.6.24-18/include/linux/module.h:494: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/linux-headers-2.6.24-18/include/linux/module.h:504: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/linux-headers-2.6.24-18/include/linux/module.h:508: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/linux-headers-2.6.24-18/include/linux/module.h:513: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/linux-headers-2.6.24-18/include/linux/module.h:523: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/linux-headers-2.6.24-18/include/linux/module.h:528: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/linux-headers-2.6.24-18/include/linux/module.h:533: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/linux-headers-2.6.24-18/include/linux/module.h:540: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/linux-headers-2.6.24-18/include/linux/module.h:545: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/linux-headers-2.6.24-18/include/linux/module.h:550: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/linux-headers-2.6.24-18/include/linux/module.h:556: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/linux-headers-2.6.24-18/include/linux/module.h:563: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/linux-headers-2.6.24-18/include/linux/module.h:568: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/linux-headers-2.6.24-18/include/linux/module.h:573: warning: empty declaration
/usr/src/linux-headers-2.6.24-18/include/linux/module.h:589: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/linux-headers-2.6.24-18/include/linux/module.h:596: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/linux-headers-2.6.24-18/include/linux/module.h:601: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/linux-headers-2.6.24-18/include/linux/module.h:606: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/linux-headers-2.6.24-18/include/linux/module.h:618: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
/usr/src/linux-headers-2.6.24-18/include/linux/module.h:621: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
hello.c:5: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
hello.c:11: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
hello.c:13:2: warning: no newline at end of file
/usr/src/linux-headers-2.6.24-18/include/linux/module.h:163: error: declaration for parameter ‘search_exception_tables’ but no such parameter
/usr/src/linux-headers-2.6.24-18/include/linux/module.h:84: error: parameter ‘__this_module’ has incomplete type
/usr/src/linux-headers-2.6.24-18/include/linux/module.h:84: error: declaration for parameter ‘__this_module’ but no such parameter
/usr/src/linux-headers-2.6.24-18/include/linux/module.h:77: error: declaration for parameter ‘sort_main_extable’ but no such parameter
/usr/src/linux-headers-2.6.24-18/include/linux/module.h:76: error: declaration for parameter ‘sort_extable’ but no such parameter
/usr/src/linux-headers-2.6.24-18/include/linux/module.h:74: error: declaration for parameter ‘search_extable’ but no such parameter
/usr/src/linux-headers-2.6.24-18/include/linux/module.h:66: error: declaration for parameter ‘cleanup_module’ but no such parameter
/usr/src/linux-headers-2.6.24-18/include/linux/module.h:65: error: declaration for parameter ‘init_module’ but no such parameter
/usr/src/linux-headers-2.6.24-18/include/linux/marker.h:127: error: declaration for parameter ‘marker_get_private_data’ but no such parameter
/usr/src/linux-headers-2.6.24-18/include/linux/marker.h:126: error: declaration for parameter ‘marker_disarm’ but no such parameter
/usr/src/linux-headers-2.6.24-18/include/linux/marker.h:125: error: declaration for parameter ‘marker_arm’ but no such parameter
/usr/src/linux-headers-2.6.24-18/include/linux/marker.h:123: error: declaration for parameter ‘marker_probe_unregister_private_data’ but no such parameter
/usr/src/linux-headers-2.6.24-18/include/linux/marker.h:119: error: declaration for parameter ‘marker_probe_unregister’ but no such parameter
/usr/src/linux-headers-2.6.24-18/include/linux/marker.h:114: error: declaration for parameter ‘marker_probe_register’ but no such parameter
/usr/src/linux-headers-2.6.24-18/include/linux/marker.h:107: error: declaration for parameter ‘__mark_empty_function’ but no such parameter
hello.c:13: error: expected ‘{’ at end of input

thanks

---

### Post by rnodal on 2008-09-29
I can tell you something, you are missing headers. Why are you compiling this as root?

Here are some links:
[http://www.cyberciti.biz/tips/compiling-linux-kernel-module.html]("http://www.cyberciti.biz/tips/compiling-linux-kernel-module.html")

[http://www.faqs.org/docs/Linux-HOWTO/Module-HOWTO.html]("http://www.faqs.org/docs/Linux-HOWTO/Module-HOWTO.html")

I hope that helps.

-r

---

### Post by mindoms on 2008-09-29
have naever played with kernel headers, and dont know what else is wrong, but
define MODULE
should be 
#define MODULE

but... -DMODULE did already define MODULE,
so #define MODULE will give you a warning

hth, stefan

---

### Post by dwhitney67 on 2008-09-29
> **kcode said:**
> ... 

define MODULE
#include <linux/module.h>

int init_module (void)
{
	printk("Hello kernel\n");
	return 0;
}

void cleanup_module (void)
{
	printk("goodbye kernel\n");
}

...

thanks
Where did you learn to write a kernel module?  Did the reference (book, website, whatever) you used not tell you how to compile/link a kernel module?  If not, I would suggest you find another reference!

Here's a complete example for a HelloWorld.c module and the Makefile that can be used to build it.  Note... you do _not_ have to be 'root' to build the kernel module.

HelloWorld.c:
[PHP]#include <linux/module.h>      // Needed by all modules

#define DRIVER_AUTHOR "dwhitney67"
#define DRIVER_DESC   "A Hello World kernel module."

MODULE_LICENSE("GPL");
MODULE_AUTHOR(DRIVER_AUTHOR);            /* Who wrote this module? */
MODULE_DESCRIPTION(DRIVER_DESC);         /* What does this module do */


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
module_exit( goodbye_world );[/PHP]

Makefile:
```
obj-m += HelloWorld.o

EXTRA_CFLAGS = -O2

all:
	$(MAKE) -C /lib/modules/`uname -r`/build M=$(PWD) modules

clean:
	$(MAKE) -C /lib/modules/`uname -r`/build M=$(PWD) clean
	$(RM) Module.markers modules.order
```

To build the HelloWorld.c kernel module, save the two files listed above, and then run the make command.
```
make
```

To insert the module into the running kernel:
```
sudo insmod HelloWorld.ko
```

To remove the module:
```
sudo rmmod HelloWorld
```

To verify the output:
```
tail /var/log/messages
```

Anyhow, this is the gist of creating, compiling, and inserting a simple module into the kernel.  I suggest you find a comprehensive guide to assist you with more complicated examples.

---

### Post by kcode on 2008-09-30
no success
reference i'm using asks me just to gcc -Wall -c hello.c

using the makefile provided i'm getting this:
make: Warning: File `Makefile' has modification time 3.8e+04 s in the future
make -C /lib/modules/`uname -r`/build M=/home/kc/Desktop/linux device drivers modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
make[1]: *** No rule to make target `device'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [all] Error 2

---

### Post by dwhitney67 on 2008-10-01
> **kcode said:**
> no success
reference i'm using asks me just to gcc -Wall -c hello.c

using the makefile provided i'm getting this:
make: Warning: File `Makefile' has modification time 3.8e+04 s in the future
make -C /lib/modules/`uname -r`/build M=/home/kc/Desktop/linux device drivers modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
make[1]: *** No rule to make target `device'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [all] Error 2
Are you attempting to build a kernel module or not?

If you are, then your reference is dead wrong!  Discard it.

From looking at the error messages generated when you invoked the Makefile, why did you run a 'make device'?  My instructions indicated that you should run 'make'.

P.S.  If you have modified the Makefile as I presented it in any way, please post it so that it can be evaluated for correctness.

---

### Post by kcode on 2008-10-01
> **dwhitney67 said:**
> Are you attempting to build a kernel module or not?

If you are, then your reference is dead wrong!  Discard it.

From looking at the error messages generated when you invoked the Makefile, why did you run a 'make device'?  My instructions indicated that you should run 'make'.

P.S.  If you have modified the Makefile as I presented it in any way, please post it so that it can be evaluated for correctness.

sorry, but i never changed your Makefile. And i ran make only, not make device.:)

---

### Post by dwhitney67 on 2008-10-01
Sorry for my suspicions.  They were based on this output statement:

*make[1]: *** No rule to make target `device'. Stop.*

Ensure that the Makefile was created properly.  The statements that start with a $(MAKE) and $(RM) should be preceded by a tab... not blank spaces.  You may have obtained blank spaces if you copied/pasted the Makefile I posted.

P.S.  I have assumed all along that you have the build tools in place.  Can you confirm by running the following:
```
sudo apt-get install build-essentials
```

---

### Post by kcode on 2008-10-02
> **dwhitney67 said:**
> 
Ensure that the Makefile was created properly.  The statements that start with a $(MAKE) and $(RM) should be preceded by a tab... not blank spaces.  You may have obtained blank spaces if you copied/pasted the Makefile I posted.

P.S.  I have assumed all along that you have the build tools in place.  Can you confirm by running the following:
```
sudo apt-get install build-essentials
```

I checked it, Makefile is fine.
well...i dont have build-essentials but build-essential
(i think you meant build-essential only:))

And when i compiled it as root, i got this:
> 
make -C /lib/modules/`uname -r`/build M= modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
make[2]: *** No rule to make target `arch/x86/kernel/asm-offsets.c', needed by `arch/x86/kernel/asm-offsets.s'.  Stop.
make[1]: *** [prepare0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [all] Error 2


---

### Post by dwhitney67 on 2008-10-02
kcode -

If you are attempting to create a new kernel module, just for test/educational purposes, you do NOT need to build it as root.

The other concern I see is that it seems you are building something more than just the "hello world" module.  Is this true?

I would expect that you would have a sub-directory under your home account that contains both the Makefile and the HelloWorld.c files.  There, as a regular user, you would run 'make'.  The output should resemble:
```

make -C /lib/modules/`uname -r`/build M=/home/userid/KernelModule modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /home/userid/KernelModule/HelloWorld.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/userid/KernelModule/HelloWorld.mod.o
  LD [M]  /home/userid/KernelModule/HelloWorld.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'

```
If you are doing something different from what I described above, then please elaborate.

---

### Post by kcode on 2008-10-02
On 'making' as root, i got some different output. Thats why i posted it.

> 
The other concern I see is that it seems you are building something more than just the "hello world" module.  Is this true?

No I am just trying to work on single hello world module.

> 
 would expect that you would have a sub-directory under your home account that contains both the Makefile and the HelloWorld.c files.  There, as a regular user, you would run 'make'.  

I am doing just this.

I think there is some problem with configuration of my kernel headers. I tried with other versions(2.6.24.16/17/18/19) also,
but none worked.
Please check this out:
```

kc@my-machine:~/kernelModule$ make
make -C /lib/modules/`uname -r`/build M=/home/kc/kernelModule modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-17-generic'
make[2]: *** No rule to make target `/home/kc/kernelModule/HelloWorld.c', needed by `/home/kc/kernelModule/HelloWorld.o'.  Stop.
make[1]: *** [_module_/home/kc/kernelModule] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-17-generic'
make: *** [all] Error 2

kc@my-machine:~/kernelModule$ sudo make
[sudo] password for kc: 
make -C /lib/modules/`uname -r`/build M= modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-17-generic'
  CHK     include/linux/version.h
  CHK     include/linux/utsrelease.h
  UPD     include/linux/utsrelease.h
  HOSTCC  scripts/basic/fixdep
  HOSTCC  scripts/basic/docproc
make[2]: *** No rule to make target `arch/x86/kernel/asm-offsets.c', needed by `arch/x86/kernel/asm-offsets.s'.  Stop.
make[1]: *** [prepare0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-17-generic'
make: *** [all] Error 2


```
[this is just killing me!!]

---

### Post by rnodal on 2008-10-02
Could you port your make file?

-r

---

### Post by dwhitney67 on 2008-10-02
Here's the problem:
```

make[2]: *** No rule to make target `/home/kc/kernelModule/HelloWorld.c', needed by `/home/kc/kernelModule/HelloWorld.o'.  Stop.

```
Either ensure that you have a file called HelloWorld.c in your current directory, or edit the Makefile so that the object file listed matches the filename you have.

Currently your Makefile has HelloWorld.o associated with the obj-m.  The C file in your current directory is not named HelloWorld.c!

And once again, you do NOT need to be root (or sudo) to run the 'make'.

---

### Post by kcode on 2008-10-02
```

obj-m += HelloWorld.o

EXTRA_CFLAGS = -O2

all:
	$(MAKE) -C /lib/modules/`uname -r`/build M=$(PWD) modules

clean:
	$(MAKE) -C /lib/modules/`uname -r`/build M=$(PWD) clean
	$(RM) Module.markers modules.order

```

---

### Post by rnodal on 2008-10-02
This may sound stupid but do you have the kernel source packages installed?

-r

---

### Post by kcode on 2008-10-02
> **dwhitney67 said:**
> Here's the problem:
```

make[2]: *** No rule to make target `/home/kc/kernelModule/HelloWorld.c', needed by `/home/kc/kernelModule/HelloWorld.o'.  Stop.

```
Either ensure that you have a file called HelloWorld.c in your current directory, or edit the Makefile so that the object file listed matches the filename you have.

Currently your Makefile has HelloWorld.o associated with the obj-m.  The C file in your current directory is not named HelloWorld.c!

And once again, you do NOT need to be root (or sudo) to run the 'make'.

I am a fool.

thanks a lot.
//And yes...i made the module as normal user
//I think i need a sleep..

---

### Post by scottptn on 2008-10-09
Hello,

I was trying to compile my first kernel module and the method shown by [dwhitney]("http://ubuntuforums.org/showpost.php?p=5878070&postcount=4") , worked like a charm . Im extremely glad i hit upon this thread in the forum .
Everything works ,but being new to kernel stuff, i need some clarification with regards to the following 2 questions which i hope someone will be kind enough to answer :

1) In the make file,the command used is :

```
make -C /lib/modules/`uname -r`/build M=$(PWD) modules
```

I understand -C means change to the directory /lib/modules/`uname -r`/build . $(PWD) refers to my present working directory,but what does M=$(PWD) modules , mean ?


2) 
```
sudo insmod HelloWorld.ko
``` , works . But instead if i use :

```
modprobe HelloWorld
```, i get the error "FATAL: Module HelloWorld not found." . Isnt modprobe , just like insmod used to add modules to the kernel ?. Whats the difference ?


Thank You .

---

### Post by dwhitney67 on 2008-10-09
> **scottptn said:**
> Hello,

I was trying to compile my first kernel module and the method shown by [dwhitney]("http://ubuntuforums.org/showpost.php?p=5878070&postcount=4") , worked like a charm . Im extremely glad i hit upon this thread in the forum .
Everything works ,but being new to kernel stuff, i need some clarification with regards to the following 2 questions which i hope someone will be kind enough to answer :

1) In the make file,the command used is :

```
make -C /lib/modules/`uname -r`/build M=$(PWD) modules
```

I understand -C means change to the directory /lib/modules/`uname -r`/build . $(PWD) refers to my present working directory,but what does M=$(PWD) modules , mean ?


2) 
```
sudo insmod HelloWorld.ko
``` , works . But instead if i use :

```
modprobe HelloWorld
```, i get the error "FATAL: Module HelloWorld not found." . Isnt modprobe , just like insmod used to add modules to the kernel ?. Whats the difference ?


Thank You .

Answers (which may not be correct!):

1)  The M=<dir> indicates where the source code for the module(s) is located at; the 'modules' indicates to 'make' what to do (i.e. create modules).

2)  Refer to the man-page for modprobe.  modprobe only looks for modules in the bowels of /lib/modules/`uname -r`, and in any directories listed in either /etc/modprobe.conf or within file(s) created in /etc/modprobe.d.

3)  (This was listed in my email message)... To insert a module during system start-up, and to rely on modprobe, see the answer to question 2.  A convenient place to list the module is in /etc/modules.

Otherwise, you will need to create a script in /etc/init.d and create a link in the appropriate run-level directory (e.g. /etc/rc5.d). The script would run the insmod.  Alternatively you can insert an insmod statement into /etc/rc.local.

---

### Post by scottptn on 2008-10-09
Thanks dwhitney . That makes it clear to me now :) .

---

### Post by Aessa on 2008-10-24
I am trying to compile the Linux Device Driver example for tty.
[http://oreilly.com/catalog/9780596005900/?CMP=AFC-ak_book&ATT=Linux+Device+Drivers](http://oreilly.com/catalog/9780596005900/?CMP=AFC-ak_book&ATT=Linux+Device+Drivers)
[http://oreilly.com/catalog/9780596005900/book/index.csp](http://oreilly.com/catalog/9780596005900/book/index.csp)
[http://examples.oreilly.com/linuxdrive3/](http://examples.oreilly.com/linuxdrive3/)

I still get the error seen in this forum regarding "no rule to make target 'Device'.

I have check filenames etc. It all seems OK. I also get different results when compiling as root, but I **do not compile as root** normally.

Can someone perhaps help me out with this?
I am also looking for a way to have this tty device communicate with a normal serial port ttyS0. The driver should simply relay data in the end, but I can't even get the example to work. This data relaying should therefore be able to use a ttyS0 or somehow other low level serial port access. I have a hard time finding info on this. Is inb() and outb() supposed to be the way? What about the existing serial driver then? How can I take over control of only one port?

---

