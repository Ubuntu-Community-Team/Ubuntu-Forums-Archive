---
title: "Writing USB Device Driver"
date: 2010-10-20
forum: Programming Talk
---

### Post by Zymus on 2010-10-20
Hello, Recently I've gained interest in writing a modular library for console controllers. What I mean by that is that I want to write a library so that you can plug in any usb enabled console controller, and be able to program the features of the controller. However, there is one small catch. I don't know how to write device drivers. So i did some research and the only things that turned up was using libhid, or libusb. Now I don't know which one is better, but in the end I just decided to use the linux/usb.h header for all my work. So, I got it to recognize the driver in the kernel, but it refuses to probe. No matter that vendor/product id combination I use for any of the devices I've tested.

cyborg.c
```

#include <linux/module.h>
#include <linux/kernel.h>
#include <linux/init.h>
#include <linux/usb.h>

#define AUTHOR "Zymus"
#define DESC "Device Driver for the Cyborg Gaming Controller"
#define VENDOR 0x06A3
#define DEVICE 0xF622

MODULE_LICENSE("GPL");
MODULE_AUTHOR(AUTHOR);
MODULE_DESCRIPTION(DESC);

static struct usb_device_id cyborg_table [] =
{
    { USB_DEVICE(VENDOR, DEVICE) },
    { }
};

MODULE_DEVICE_TABLE(usb, cyborg_table);

int cyborg_probe(struct usb_interface *intf, const struct usb_device_id *id)
{
    printk(KERN_INFO "CYBORG_PROBE");
    return 0;
}

void cyborg_disconnect(struct usb_interface *intf)
{
    printk(KERN_INFO "CYBORG_DISCONNECT");
}

static struct usb_driver cyborg_driver =
{
    name:        "cyborg",
    id_table:    cyborg_table,
    probe:        cyborg_probe,
    disconnect:    cyborg_disconnect,
};

static int __init init_cci(void)
{
    int result = usb_register(&cyborg_driver);
    if(result < 0)
    {
        printk(KERN_INFO "usb_register failed. err #%d", result);
        return -1;
    }
    printk(KERN_INFO "INIT_CYBORG");
    return 0;
}

module_init(init_cci);

static void __exit exit_cci(void)
{
    printk(KERN_INFO "EXIT_CYBORG");
    usb_deregister(&cyborg_driver);
}

module_exit(exit_cci);

```

modinfo cyborg.ko
> 
filename:       ./cyborg.ko
description:    Device Driver for the Cyborg Gaming Controller
author:         Zymus
license:        GPL
srcversion:     BFB05FBC01AD25EC4226386
alias:          usb:v06A3pF622d*dc*dsc*dp*ic*isc*ip*
depends:        
vermagic:       2.6.32-25-generic-pae SMP mod_unload modversions 586TSC 


lsusb
> 
Bus 008 Device 002: ID 06a3:8021 Saitek PLC Eclipse II Keyboard
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 006: ID 06a3:f622 Saitek PLC <-- This is the console controller
Bus 006 Device 004: ID 046d:c408 Logitech, Inc. Marble Mouse (4-button)
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


lsmod
> 
Module                  Size  Used by
cyborg                  1072  0 
...


dmesg
> 
[  973.236923] usbcore: registered new interface driver cyborg
[  973.236926] INIT_CYBORG


dmesg when plugging in device
> 
[ 1081.689012] usb 6-1: new full speed USB device using uhci_hcd and address 7
[ 1081.850274] usb 6-1: configuration #1 chosen from 1 choice
[ 1081.857250] input: Cyborg V.3 Rumble Pad as /devices/pci0000:00/0000:00:1d.0/usb6/6-1/6-1:1.0/input/input11
[ 1081.857328] generic-usb 0003:06A3:F622.0008: input,hidraw0: USB HID v1.11 Joystick [Cyborg V.3 Rumble Pad] on usb-0000:00:1d.0-1/input0


modprobe cyborg/cyborg.ko/Cyborg
> 
FATAL: Module cyborg not found.



Any ideas on this matter would be great. Thank you.

---

### Post by jamesbon on 2010-10-20
Please post your make file and on which kernel version are you trying this?

---

### Post by Zymus on 2010-10-20
uname -r
> 
2.6.32-25-generic

Makefile
```

obj-m += cyborg.o

all:
    make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules

clean:
    make -C /lib/modules/$(shell uname -r)/build M=$(PWD) clean


```

---

### Post by Zymus on 2010-10-20
Any ideas?

---

### Post by jamesbon on 2010-10-21
No I could not find the error in your program though I suggest following  links you can check these pages
[http://paste.org/pastebin/view/1871](http://paste.org/pastebin/view/1871)
[http://forums.techguy.org/software-development/674178-write-linux-usb-driver.html](http://forums.techguy.org/software-development/674178-write-linux-usb-driver.html)
[http://www.linuxjournal.com/article/7353](http://www.linuxjournal.com/article/7353)
[http://www.kroah.com/linux/talks/ols_2005_driver_tutorial/mgp00010.html](http://www.kroah.com/linux/talks/ols_2005_driver_tutorial/mgp00010.html)
[http://matthias.vallentin.net/2007/04/writing-linux-kernel-driver-for-unknown.html](http://matthias.vallentin.net/2007/04/writing-linux-kernel-driver-for-unknown.html)
[http://www.google.com/search?client=ubuntu&channel=fs&q=how+to+write+usb+driver+for+linux&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=how+to+write+usb+driver+for+linux&ie=utf-8&oe=utf-8)
I am not sure as how much will my links will help you since I am also new to USB driver development.

---

### Post by Zymus on 2010-10-22
Another strange symptom: It will randomly start probing... To my knowledge i didn't do anything, bud looking at dmesg indicated that it was indeed probing the device. I rmmod, and then insmod, and it stops working :(

---

### Post by jamesbon on 2010-10-22
Are you using device ids of existing devices that already have drivers
bound to them?  If so, don't do that :)

---

### Post by Zymus on 2010-10-22
I don't believe so. IT's a game pad so it might be bound to the joystick service?

EDIT: Hmm, is there a way to "supercede" the usbhid driver? so that it checks my driver and if it doesn't find it, then pass it to the usbhid?

---

### Post by jamesbon on 2010-10-24
> **Zymus said:**
> I don't believe so. IT's a game pad so it might be bound to the joystick service?

You can see if it is, look in sysfs, or in /sys/kernel/usb/devices
> **Zymus said:**
> EDIT: Hmm, is there a way to "supercede" the usbhid driver?
 Yes, look at the hid driver blacklist.
> **Zymus said:**
> 
so that it checks my driver and if it doesn't find it, then pass it to the usbhid?
If your driver is loaded first, yes, you can do that.

You can unbind the device from the hid driver by hand through sysfs and
then load your driver for testing.

---

### Post by Zymus on 2010-10-25
Okay, i found my device in /dev/bus/usb/devices/usb6/6-1. When I nano idVendor, i see the correct vendor, and when i nano idProduct, i see the correct product. So it's definately there, but I think the problem is that usbhid is catching it before my module does. how would i unload the device and test like you stated?

---

