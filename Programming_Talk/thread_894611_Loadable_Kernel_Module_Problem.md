---
title: "Loadable Kernel Module Problem"
date: 2008-08-19
forum: Programming Talk
---

### Post by tdz on 2008-08-19
I'm a relatively new Ubuntu (and Linux) developer. My current project is attempting to port a framebuffer driver for a small LCD display. This is for the 2.6.24 kernel (Ubuntu 8.04)

Apparently, I am have a Makefile problem of some sort with the driver that I am attempting to port and modify.

I have been able to use KDevelop to build the default "Hello World" module. I can get this module to install and uninstall using insmod / rmmod without a problem.

When I work with my fb module though, weird things happen.

If I use the (slightly modified) "Hello World" Makefile, the module builds fine in KDevelop. If I examine the hexl-mode display of the .ko file in Emacs, the MODULE_LICENSE("GPL") makes it in fine. However, neither insmod nor modprobe recognizes this as a module and, as a result, neither will load it. I have copied the .ko file to /lib/modules/<kernel - version> for modprobe. Still no joy.

If I try building with a Makefile that a colleague gave me from another driver, again the module builds properly in KDevelop. This time, insmod recognizes that it is a module, but says there are "Unknown symbols in module". (The first attempt (only) to install the module with insmod after a boot says "module license 'unspecified' taints kernel.' before the unknowns are displayed - the unknowns are displayed every time I use insmod on this module.) The unknowns (displayed in dmesg) are in the System.map and Module.symvers from my kernel build (exported as GPL symbols). The Emacs hexl-mode display of this .ko DOES NOT show the GPL module license (although the MODULE_LICENSE("GPL") macro is right where it was in the other build. Modprobe gives me a "FATAL: Module xxx not found" error if I try to use it to install the fb module.

My main question is what do I need to do to the Makefile (probably my colleague's Makefile) to get or keep the MODULE_LICENSE (and AUTHOR and DESCRIPTION)in the .ko file? If that doesn't resolve the unknown symbols, what do I need to do about that? A secondary question would be what do I need to do to the fairly bare bones Makefile from "Hello World" to use it to build my driver?

If anyone has any advice, I'd really appreciate it. I'm not sure what else to try. (My colleague has no idea what is going on, so I figured I need to get some help from someone out there.)

Thanks in advance.

---

