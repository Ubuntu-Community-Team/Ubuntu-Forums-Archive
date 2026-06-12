---
title: "What software to use to control relay on SainSmart USB 4-channel relay board for auto"
date: 2014-10-06
forum: New to Ubuntu
---

### Post by cigtoxdoc on 2014-10-06
I am posting in Newbie section because I do not know what I am doing.  I have a SainSmart USB 4-channel relay board for automation.  This board is based on the FTDI 245R chip.  The command lsusb gives: Bus 002 Device 004: ID 0403:6001 Future Technology Devices International, Ltd FT232 USB-Serial (UART) IC.  What applications software do I use to make one of the four relays start and repeat the following series of events for 300 seconds: relay closed for 3 seconds then relay opens for 27 seconds.  I don't think that this is "rocket science" but no one seems to know the answer.  Is there a graphical application that makes such programming easy?  PC is running Ubuntu 14.04 64-bit.

Thank you,

John

---

### Post by matt_symes on 2014-10-06
Hi

> **cigtoxdoc said:**
> I am posting in Newbie section because I do not know what I am doing.  I have a SainSmart USB 4-channel relay board for automation.  This board is based on the FTDI 245R chip.  The command lsusb gives: Bus 002 Device 004: ID 0403:6001 Future Technology Devices International, Ltd FT232 USB-Serial (UART) IC.  What applications software do I use to make one of the four relays start and repeat the following series of events for 300 seconds: relay closed for 3 seconds then relay opens for 27 seconds.  I don't think that this is "rocket science" but no one seems to know the answer.  Is there a graphical application that makes such programming easy?  PC is running Ubuntu 14.04 64-bit.

Thank you,

John

Interesting piece of kit. Can i ask what you intend to do with it ?

Anyway you will need a kernel modules for it. There looks to be 2 kernel modules on my machine for ftdi. This is a new kernel but the modules are also in the 3.13 kernels i have on this machine.

```
matthew-laptop:/home/matthew:2 % find /lib/modules/$(uname -r) -name "*ftdi*"
/lib/modules/3.16.3-031603-generic/kernel/drivers/usb/misc/ftdi-elan.ko
/lib/modules/3.16.3-031603-generic/kernel/drivers/usb/serial/ftdi_sio.ko
matthew-laptop:/home/matthew:2 %
```

Getting some info on the drivers reveals

```
matthew-laptop:/home/matthew:2 % modinfo ftdi_sio | grep description
description:    USB FTDI Serial Converters Driver
matthew-laptop:/home/matthew:2 % modinfo ftdi_elan | grep description 
description:    FTDI ELAN driver
matthew-laptop:/home/matthew:2 % 
```

> Future Technology Devices International, Ltd FT232 USB-Serial (UART) IC

So i suspect (and assume) the first kernel module is the one that may be of interest for you as the above quote from your first post suggests you communicate with the board using serial over USB.

To load the module....

```
sudo modprobe ftdi_sio
```

or maybe

```
sudo modprobe ftdi_sio vendor=0403 product=6001
```

I would start investigating that kernel module to see if it can communicate with the board and to see if that does what you need. So you need to do some research to see if this is the correct kernel module.

Anyway, with the board connected and assuming the kernel module is the correct module to communicate with the board, udev should create a device node in /dev.

It will be something like ttyUSB so look for a device by trying this

```
ls -l /dev/ttyUSB*
```

You would talk to the board via that device node.

Anyway, it is now 4.30am here and i am just about to logoff.

We can continue this tomorrow.

**EDIT:**

It does look like this is the correct kernel module for your board as the vendor id and product id match.

```
matthew-laptop:/home/matthew:2 % modinfo ftdi_sio | grep 6001        
alias:          usb:v05D1p6001d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1A79p6001d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1BC9p6001d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v**0403p6001**d*dc*dsc*dp*ic*isc*ip*in*
matthew-laptop:/home/matthew:2 %
```

Kind regards

---

