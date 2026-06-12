---
title: "Loadable Kernel Module Problem"
date: 2008-08-19
forum: Programming Talk
---

### Post by tdz on 2008-08-19
I'm a relatively new Ubuntu (and Linux) developer.  My current project is attempting to port a framebuffer driver for a small LCD display.  This is for the 2.6.24 kernel (Ubuntu 8.04)

Apparently, I am have a Makefile problem of some sort with the driver that I am attempting to port and modify.

I have been able to use KDevelop to build the default "Hello World" module.  I can get this module to install and uninstall using insmod / rmmod without a problem.

When I work with my fb module though, weird things happen.

If I use the (slightly modified) "Hello World" Makefile, the module builds fine in KDevelop.  If I examine the hexl-mode display of the .ko file in Emacs, the MODULE_LICENSE("GPL") makes it in fine.  However, neither insmod nor modprobe recognizes this as a module and, as a result, neither will load it. I have copied the .ko file to /lib/modules/<kernel - version> for modprobe.  Still no joy.

If I try building with a Makefile that a colleague gave me from another driver, again the module builds properly in KDevelop.  This time, insmod recognizes that it is a module, but says there are "Unknown symbols in module".  (The first attempt (only) to install the module with insmod after a boot says "module license 'unspecified' taints kernel.' before the unknowns are displayed - the unknowns are displayed every time I use insmod on this module.)  The unknowns (displayed in dmesg) are in the System.map and Module.symvers from my kernel build (exported as GPL symbols).  The Emacs hexl-mode display of this .ko DOES NOT show the GPL module license (although the MODULE_LICENSE("GPL") macro is right where it was in the other build.  Modprobe gives me a "FATAL: Module xxx not found" error if I try to use it to install the fb module.

My main question is what do I need to do to the Makefile (probably my colleague's Makefile) to get or keep the MODULE_LICENSE (and AUTHOR and DESCRIPTION)in the .ko file?  If that doesn't resolve the unknown symbols, what do I need to do about that?  A secondary question would be what do I need to do to the fairly bare bones Makefile from "Hello World" to use it to build my driver?

If anyone has any advice, I'd really appreciate it.  I'm not sure what else to try.  (My colleague has no idea what is going on, so I figured I need to get some help from someone out there.)

Thanks in advance.

---

### Post by dstew on 2008-08-19
Wow, not exactly an "absolute beginner" question. You might try posting in the [Programming Talk forum]("http://ubuntuforums.org/forumdisplay.php?f=39"). It is fairly active, and prowled by programmers regularly.

---

### Post by tdz on 2008-08-19
Thank you.  I'm a relative beginner (with Linux and Ubuntu, not with software development though).  I'll do acut-n-paste and see what happens over there.

---

### Post by sdennie on 2008-08-19
Moved to Programming Talk

---

### Post by jinksys on 2008-08-19
Could you upload a source tar of the lcd buffer driver so we could have a look at it?

---

### Post by dwhitney67 on 2008-08-19
> **tdz said:**
> I'm a relatively new Ubuntu (and Linux) developer.  My current project is attempting to port a framebuffer driver for a small LCD display.  This is for the 2.6.24 kernel (Ubuntu 8.04)

Apparently, I am have a Makefile problem of some sort with the driver that I am attempting to port and modify.

I have been able to use KDevelop to build the default "Hello World" module.  I can get this module to install and uninstall using insmod / rmmod without a problem.

When I work with my fb module though, weird things happen.

If I use the (slightly modified) "Hello World" Makefile, the module builds fine in KDevelop.  If I examine the hexl-mode display of the .ko file in Emacs, the MODULE_LICENSE("GPL") makes it in fine.  However, neither insmod nor modprobe recognizes this as a module and, as a result, neither will load it. I have copied the .ko file to /lib/modules/<kernel - version> for modprobe.  Still no joy.

If I try building with a Makefile that a colleague gave me from another driver, again the module builds properly in KDevelop.  This time, insmod recognizes that it is a module, but says there are "Unknown symbols in module".  (The first attempt (only) to install the module with insmod after a boot says "module license 'unspecified' taints kernel.' before the unknowns are displayed - the unknowns are displayed every time I use insmod on this module.)  The unknowns (displayed in dmesg) are in the System.map and Module.symvers from my kernel build (exported as GPL symbols).  The Emacs hexl-mode display of this .ko DOES NOT show the GPL module license (although the MODULE_LICENSE("GPL") macro is right where it was in the other build.  Modprobe gives me a "FATAL: Module xxx not found" error if I try to use it to install the fb module.

My main question is what do I need to do to the Makefile (probably my colleague's Makefile) to get or keep the MODULE_LICENSE (and AUTHOR and DESCRIPTION)in the .ko file?  If that doesn't resolve the unknown symbols, what do I need to do about that?  A secondary question would be what do I need to do to the fairly bare bones Makefile from "Hello World" to use it to build my driver?

If anyone has any advice, I'd really appreciate it.  I'm not sure what else to try.  (My colleague has no idea what is going on, so I figured I need to get some help from someone out there.)

Thanks in advance.
This I believe is easiest Makefile there is:
```
obj-m += YourDriverName.o

EXTRA_CFLAGS = -O2

all:
        $(MAKE) -C /lib/modules/`uname -r`/build M=$(PWD) modules

clean:
        $(MAKE) -C /lib/modules/`uname -r`/build M=$(PWD) clean
        $(RM) Module.markers modules.order
```
Replace 'YourDriverName' with the name of your driver file.

If your driver builds, then try to 'insmod' it.
```
$ sudo insmod YourDriverName.ko
```
To remove it:
```
$ sudo rmmod YourDriverName
```

---

### Post by tdz on 2008-08-20
I tried the modified makefile.  No joy.

It blew away my kernel build (bzImage) (I do have a backup, though).

After it rebuilt all the modules, I ended up with something similar to what I had before when I attempted to load the module:

dmesg showed
no version for "struct_module" found:  Kernel tainted."

(It should be noted that the GPL license info DID show up in the hexl-mode dump of the .ko file.)


insmod gave me
"error inserting 'm9kdispfb.ko': -1 No such device or address"

modprobe gave
"FATAL: Module m9kdispfb not found."

As jinksys requested, I've attached a .tar of the directory.  There are 4 flavors of Makefile there:

Makefile.small is the makefile dwhitney67 suggested.
Makefile.test is the modified makefile generated for the "Hello World" kernel module by KDevelop
Makefile.new and Makefile.save are variants of the makefile from my colleague.

.new and .save do NOT appear to store the GPL license info in the .ko file, the others do.  .test does not appear to create a module for this driver (though it works fine for "Hello World") - at least insmod will not even attempt to load it.  insmod attemts to load the others, but fails.  According to dmesg, the .new and .save makefiles have the "tainted kernel" message along with several undefined symbols.  The .small makefile produces the dmesg above.

The source file I am working with is essentially an unmodified (or only slightly modified) linux/drivers/video/arcfb.c from the 2.6.24 source tree.

I'm curious - could my problem be more of a .config problem than a Makefile problem?  Are there some critical items in the kernel .config that could be wrong?  Since this is really my first go-round on all of this, I sure wouldn't want to rule that out, especially since I had a lot of trouble building a kernel that would boot and that had proper network access.  If you think that is the case, the same question applies:  What do you suggest that I try next?  (If anyone is familiar with the various framebuffer drivers available - either in the video directory here or somewhere else and you want to point me to one that you think will work well (likely after some mods to work with our lcd display hardware) please feel free to let me know.)

As always, thanks in advance.

---

### Post by dwhitney67 on 2008-08-20
Have you tried building/inserting your kernel module without modifying the existing kernel your system came installed with?

For test purposes, you should be able to build a kernel module in user-space; it does not need to be built in the same directory where the kernel source code resides.  Of course, you will require super-user privileges to insert/remove the module.

It has been awhile since I have kept up with new kernel development, but the GPL license thing is not a requisite to insert/remove a kernel module.

I am running kernel 2.6.25.14 (-108.fc9.i686) on my Fedora 9 system, and 2.6.24-19-generic on my Ubuntu 8.04 system.  In both systems I am able to make and insert/remove the following kernel modules without any hassles.

HelloWorld.c:
[PHP]#include <linux/module.h>      // Needed by all modules

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
uname_ix86.c:
[PHP]/*
 *      This simple piece of code simply turns your ix86 into a i586 -
 *      useful if you're cross-compiling for a weaker platform.
 *
 *      Based on the program contained in the cross compiling hint by
 *      Daniel Baumann <danielbaumann@linuxmail.org>
 *                              
 *      Originally Updated to 2.6.x series kernel by Roel Neefs.
 *
 *      Updated to work with the 2.6.x series kernel driver standards
 *      by Jim Gifford.
 *
 *      You will need to create a small Makefile for this module to 
 *      work.
 *
 *              cat > Makefile << "EOF"
 *              obj-m += uname_ix86.o
 *              EOF
 *
 *      To compile as a module use the following command:
 *
 *              make -C /usr/src/linux-{version} SUBDIRS=$PWD
 *
 *      You can change the UNAME_DUMB_STEPPING variable to get the following
 *      results
 *
 *              2 = 286         3 = 386         4 = 486         5 = 586         6 = 686
 *                                                                                      
 */

#include <linux/module.h>
#include <linux/init.h>
#include <linux/utsname.h>

#ifndef UNAME_DUMB_STEPPING
        #define UNAME_DUMB_STEPPING '5';
#endif

static int save;
static int __init uname_hack_init_module( void )
{
  save = utsname()->machine[1];
  utsname()->machine[1] = UNAME_DUMB_STEPPING;
  return( 0 );
}

static void __exit uname_hack_cleanup_module( void )
{
  utsname()->machine[1] = save;
}

module_init(uname_hack_init_module);
module_exit(uname_hack_cleanup_module);[/PHP]

---

### Post by tdz on 2008-08-20
Thanks for the suggestion....

What started the journey into kernel builds was the combination of "tainted kernel" and "unresolved symbols".

The KDev "Hello World" worked fine on the original kernel that I had.  the m9kdispfb module had the problems.  When I checked the Symbol.map and Module.symvers, these symbols were indeed missing.  I suspect that some things were not needed and were not configured in the original kernel (arcfb apparently wasn't configured either or it should've had similar problems).

I'm especially confused about why "MODULE_LICENSE("GPL");", for example, is clearly in the source file but, with some makefiles, "license=GPL" is in the .ko file while with others it isn't.  Obviously there is some difference in the makefiles (since the source file is the same) which produces this effect.  In turn, this sets up the "tainted kernel" and, I suspect, the undefined symbols (since the symbols show up as EXPORT_SYMBOL_GPL in Module.symvers and in the source files where they are defined.

I am also confused about why the makefile from "Hello World" produces a loadable module there, but, when used with my module, although it includes the GPL info, it produces a .ko file which insmod does not recognize as a module.

As I said, this seems weird - and it has me running in circles.

We started with the 2.6.24-16-generic kernel.  The kernel I am currently working with (loaded with synaptic) apparently is 2.6.24.19.21  I have the headers for the older kernel, but not the source tree.  The documentation I have on kernel modules says that now (after 2.4?) the headers aren't enough - I need the source tree also.

As I said, I'm new to this process with Linux.  Some of what I am experiencing feels like wandering in the swamp without a compass or map.

The community has helped, and I do want to thank you all again.  I suspect that, once I finally get this to work, I will wind up wondering what was so hard about everything.  I haven't arrived at that point yet.

Thanks, again.

---

### Post by dwhitney67 on 2008-08-20
There are two ways I know of to get rid of the "taint" message.

1)
[PHP]
MODULE_LICENSE("GPL");
[/PHP]
2)
[PHP]#define DRIVER_AUTHOR "Jim Nasium <jnasium@aol.com>"
#define DRIVER_DESC   "A Hello World kernel module."

MODULE_AUTHOR(DRIVER_AUTHOR);            /* Who wrote this module? */
MODULE_DESCRIPTION(DRIVER_DESC);         /* What does this module do */[/PHP]
But frankly, the "taint" message is not a tremendous thing to worry about.  I get on my system when the ATI video driver (fglrx) is loaded; and yet the driver works like a charm.

P.S.  See the attached document.  It may help you.

---

### Post by jinksys on 2008-08-20
This is interesting.

I have a feeling the problem lies with your code, not your Makefile.  You have a header file that you don't even reference, and it seems important.  I am able to compile a generic "hello world" kernel module with the same makefile, so I know it's good.

I mean, why is m9kdispfb.h in the tarball if you don't include it?

---

### Post by tdz on 2008-08-20
Thanks, again.

The 'MODULE_LICENSE("GPL");' is in the code.  I'm not sure why it is picked up with some makefiles (but I don't end up with a module) but not with others. :confused:

I know a module that "taints the kernel" SHOULD load - unless it needs symbols which were exported as GPL symbols (mine does need GPL symbols).  In that case, as I understand the documentation, the module can't use GPL symbols - and insmod is smart enough to deal with that (apparently by not loading the module).

I did discover something a few minutes ago and I'm chasing that now.

In the makefile which makes the module - but doesn't seem to pick up the GPL license - there is a line

"EXTRA_CFLAGS += -I$(LDDINC)"

LDDINC is not defined at that point (and is never actually used anywhere else in the makefile).  If I comment the line out, I get the GPL license info in the .ko file hexl-mode dump, but insmod doesn't think this is a module.  If I don't comment this out, insmod thinks I have a module with undefined symbols and no GPL license in the .ko file.

Perhaps, if can I determine what LDDINC needs to be and set it to the proper include directory (and maybe find a useful way to use it with the actual make command) I might get past this problem.  In any case, this line seems to be a big part of my problem.

Does this make any sense to any of you out there?

Again, thanks in advance.

One more lap around the makefile....

---

### Post by tdz on 2008-08-20
Thanks, jinksys.  I hadn't noticed this (as I said, this was something passed on to me by someone else).  This certainly may be a problem (at the very least, it's bad form to carry stuff like unused include files around - and quite confusing besides).  I suspect that m9kdispfb.h will need to be used instead of arcfb.h (m9kdispfb is derived from, and at the moment really is still arcfb.c, for all practical purposes.)  It may turn out that the include file switchover will have more to do with supporting our lcd display than anything else (part of draining the swamp - but first I need to get out of my staring match with the 'gator).

I did find something in the makefile (see my reply to dwhitney67).  This appears to cause the module / no module, GPL / no GPL situation I've been seeing.

So, it looks like this issue of the include file is another bug to chase.  It may not have any relation to the module bug - but those are also famous last words...

---

