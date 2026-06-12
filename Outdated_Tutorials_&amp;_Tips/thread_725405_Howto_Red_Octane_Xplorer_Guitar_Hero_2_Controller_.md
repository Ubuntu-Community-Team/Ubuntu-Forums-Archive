---
title: "Howto: Red Octane Xplorer Guitar Hero 2 Controller in Ubuntu Gutsy (x86 and x64)"
date: 2008-03-15
forum: Outdated Tutorials &amp; Tips
---

### Post by jlapaglia on 2008-03-15
I had to look in a few posts to find the solution, and the answer came from all of them, I am putting it all into one post for everyone else that can't figure this out.

This guide works on both x64 and x86 architecture.

First the **_dependencies for compiling:_**

```
sudo apt-get install linux-headers-'uname -r' build-essential
sudo apt-get install automake1.9
```

now we need to _**download a few files for the driver:**_

mkdir ~/.xpad360
[http://xbox-linux.cvs.sourceforge.net/*checkout*/xbox-linux/kernel-2.6/drivers/usb/input/xpad.c](http://xbox-linux.cvs.sourceforge.net/*checkout*/xbox-linux/kernel-2.6/drivers/usb/input/xpad.c)
[http://xbox-linux.cvs.sourceforge.ne...b/input/xpad.h](http://xbox-linux.cvs.sourceforge.ne...b/input/xpad.h)

now _**Create the Makefile:**_
```
gedit ~/.xpad360/Makefile
```

and place this into the file:

```
KERNEL_DIR?=/usr/src/linux-headers-2.6.22.14-generic

obj-m := xpad.o

EXTRA_CFLAGS= -I$(shell pwd)

all:
	$(MAKE) modules -C $(KERNEL_DIR) SUBDIRS=$(shell pwd)
```

(if someone could tell me what i should put in the make file turn the linux-headers version into a variable it would help future proof this method)

Save the file.

now to [U][B]Compile and Insert the Drivers
[/B][/U]

```
sudo make
```

```
sudo cp -f xpad.ko /lib/modules/$(uname -r)/kernel/drivers/input/joystick/
```

```
sudo depmod -a
sudo modprobe xpad
```

I had mixed results with rebooting before I tried the controller in Frets On Fire, so I'd recommend it. I'm still a linux noob so don't ask ;).

Like I said before, I don't take any credit for this guide, I just took parts from all of the ones that helped me.

---

### Post by mlapaglia on 2008-03-24
I would just like to say anyone needing help with this should feel free to contact me, (not my brother jlapaglia).. He asked me to set up the controller on his computer, and I accidently posted under his name. It's all good though!

FYI Frets on Fire is crazy awesome

---

### Post by kanorshkan on 2008-12-21
I could use some help with this. could you email me on it? 
[email]kanorshkan@yahoo.com[/email]

---

### Post by SkyWulf on 2009-04-07
Sorry, I'm a bit new here, I try
 sudo cp -f xpad.ko /lib/modules/$(uname -r)/kernel/drivers/input/joystick/
and I get 
cp: cannot stat `xpad.ko': No such file or directory
What am I doing wrong?

---

