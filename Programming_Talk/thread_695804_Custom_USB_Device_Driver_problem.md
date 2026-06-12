---
title: "Custom USB Device Driver problem"
date: 2008-02-13
forum: Programming Talk
---

### Post by mrcdsix on 2008-02-13
I have a USB device that I have created a driver for. I am having trouble though when I reboot the machine or the device (or unplug and  plug in) I get errors when running a test app for the device saying that it could not open the device.

Here is the makefile that I use to build and install the driver for the device:

```

obj-m   := vcom.o

KERNELDIR ?= /lib/modules/$(shell uname -r)/build
PWD       := $(shell pwd)
INSTALLDIR ?= /lib/modules/$(shell uname -r)/kernel/drivers/usb/misc
all:
        $(MAKE) -C $(KERNELDIR) M=$(PWD)

install:
        @echo 'must be signed in as root'
        @echo 'copying vcom.ko to $(INSTALLDIR)'
        install -m 644 vcom.ko $(INSTALLDIR)/vcom.ko
        depmod
        modprobe vcom

clean:
        rm -rf *.o *~ core .depend .*.cmd *.ko *.mod.c .tmp_versions

```


When I run "make" and "make install" the module gets loaded. 
When I plug the device in I can see it as "/dev/vcom0".  

When I run my test app I get an error that includes the following: "Can't open /dev/vcom0"

If I manually set the permissions on /dev/vcom0 (to say 666) I can run my test app. However, I can only run it once since at the end it tests a software reboot and when the device reboots the permissions on /dev/vcom0 is not accessible. Same thing happens on system reboot.

I should also note that this is my first attempt at writing a Linux driver. So if anyone has any ideas of steps I may have missed please let me know. Also, this method of "installation" works properly on FC7 and FC3 and older Debian installation. 

Thanks in advance!

---

