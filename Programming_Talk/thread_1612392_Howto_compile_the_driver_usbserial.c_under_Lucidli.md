---
title: "Howto: compile the driver usbserial.c under Lucid/linux 2.6"
date: 2010-11-03
forum: Programming Talk
---

### Post by sdaau on 2010-11-03
Hi all, 

If you're getting warnings like below (as in [hi,how ever to compile the driver usbserial.c under linux 2.6.27?thx - CodeGuru Forums](http://www.codeguru.com/forum/showthread.php?t=483788)) 
```

WARNING: "usb_serial_generic_device" [/root/RTU/youxq/usbserial/usbserial.ko] undefined!
WARNING: "usb_serial_generic_register" [/root/RTU/youxq/usbserial/usbserial.ko] undefined!
WARNING: "usb_serial_bus_type" [/root/RTU/youxq/usbserial/usbserial.ko] undefined!

```

here is the sequence of command that I run in a new folder (Makefile included in them), in order to get it to set up all files succesfully:
```

wget "http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-lucid.git;a=blob_plain;f=drivers/usb/serial/usb-serial.c" -O usb-serial.c
wget "http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-lucid.git;a=blob_plain;f=drivers/usb/serial/usb_debug.c" -O usb_debug.c
wget "http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-lucid.git;a=blob_plain;f=drivers/usb/serial/pl2303.h" -O pl2303.h
wget "http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-lucid.git;a=blob_plain;f=drivers/usb/serial/generic.c" -O generic.c
wget "http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-lucid.git;a=blob_plain;f=drivers/usb/serial/bus.c" -O bus.c
wget "http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-lucid.git;a=blob_plain;f=drivers/usb/serial/console.c" -O console.c
# wget "http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-lucid.git;a=blob_plain;f=drivers/usb/serial/ezusb.c" -O ezusb.c


cat > Makefile <<EOF
CONFIG_MODULE_FORCE_UNLOAD=y

# debug build:
# "CFLAGS was changed ... Fix it to use EXTRA_CFLAGS."
EXTRA_CFLAGS=-g -O0

obj-m += usbserial.o

usbserial-obj-y		+= console.o
usbserial-obj-n		+= ezusb.o

usbserial-objs  := usb-serial.o generic.o bus.o

all:
	make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules

clean:
	make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean
EOF


# make

# sudo mkdir /lib/modules/2.6.32.15+drm33.5-dbglucid/kernel/drivers/usb/serial
# sudo ln -s /media/nonos/AudioArduino/src/usb-serial/usbserial.ko /lib/modules/2.6.32.15+drm33.5-dbglucid/kernel/drivers/usb/serial
# sudo depmod

``` 

... after that, just run 'make' and the kernel module should build OK ; and if this driver was not present on the kernel previously, the last sequence of commands may be of use too. 

Hope this helps someone,
Cheers!

---

