---
title: "Block Driver insmod problems"
date: 2007-10-15
forum: Programming Talk
---

### Post by allenb on 2007-10-15
I am working on creating a block device driver for a "virtual" device and am running into a problem with insmod that perhaps someone else out there has had before.

My driver's main file is a stripped-down version of the simple block driver example from the book Linux Device Drivers (with the read and write functions replaced with stubs, my device needs only ioctl).  The utility functions that do all the work for the driver are included in several separate C files.

The main .c file does not (yet) call any of these external functions.  When my makefile  only uses the main .c file, the module builds correctly; I can insmod it and see the debug output appear in the system logs as well as when I rmmod it.  It also shows up in /proc/modules and /proc/devices.  However, the problem appears when I link the other .c files when the module builds.  The module builds correctly, I can insmod and rmmod it as expected, and it shows up in /proc/modules.  However, the debug (printk) output from the module_init and module_exit functions does not appear, and there is no entry in /proc/devices.

The extra .c files are not (yet) accessed in any way, it's essentially linking dead weight onto a known working block device driver, and now it's silently encountering some sort of problem that keeps the kernel from registering it as a device.

No matter how high of a priority I pass to printk, I get no debug output at all, which makes it very difficult for me to figure out what is going wrong.  All I have to do is comment out the "module-objs += xxxx.o" lines in my Makefile and the driver behaves normally.

Has anyone encountered a problem like this before?  Or, does anyone have any advice on how to get debug output out of a block device driver to diagnose a problem during module load/unload when printk fails?  Thanks for taking the time to read this

---

### Post by allenb on 2007-10-16
In reply to my own question, here is another interesting (and hopefully useful) tidbit that I discovered.

If I take the contents of all of my various .c files and copy them into the .c file that contains the driver code, the module will build, insmod, and rmmod correctly (including printk output) and will show up in /proc/modules and /proc/devices.  That makes my big .c file almost 30K lines long (which neither my editor nor my sanity enjoy working with), but at least it works.

Here is the relevant contents of my Makefile, perhaps I am missing something in the way I am linking the external C files with the main C file.

```

ifneq ($(KERNELRELEASE),)
	myModule-objs := modLibA.o modLibB.o modLibC.o
	obj-m := myModule.o
else
.PHONY : clean
CC := gcc
OS_KERNEL := $(shell uname -r)
KERNELDIR ?= /lib/modules/$(OS_KERNEL)/build
ADDCFLAG = -I$(KERNELDIR)/include
PWD := $(shell pwd)
EXTRA_CFLAGS := -Wno-strict-prototypes
LINK_FLAGS := -Wl-L./ -Wl,--no-undefined -Wl,--no-allow-shlib-undefined

default:
	$(MAKE) -C $(KERNELDIR) M=$(PWD) $(EXTRA_CFLAGS) $(LINK_FLAGS) modules
clean:
	rm -f *.o
	rm -f .*o.d
	rm -f .*o.cmd
	rm -f *.mod.?
	rm -f *~
	rm -f *.ko

# Rule for building any .c into a .o
%.o: %.c
	$(CC) -c $(ADDCFLAG) -D__KERNEL__ -o $@ $<

endif

```

---

### Post by allenb on 2007-11-05
Aha, the solution was a subtle one.  It turns out that the name of the module cannot be the name of one of the .c files. My main .c file was myModule.c and I was compiling the module to myModule.ko. I changed
```

myModule-objs := modLibA.o modLibB.o modLibC.o
	obj-m := myModule.o

```
to
```

myCustomModule-objs := myModule.o modLibA.o modLibB.o modLibC.o
	obj-m := myCustomModule.o

```
and the module compiles as expected.

---

