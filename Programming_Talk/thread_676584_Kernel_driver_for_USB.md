---
title: "Kernel driver for USB"
date: 2008-01-23
forum: Programming Talk
---

### Post by rockballad on 2008-01-23
Hi there,

I know the title is so general, but there're some questions (interested ones I think :biggrin:) in this field, glad to discuss with your guys here. 

First please take a look at the source code:
[http://paste.org/index.php?id=1871](http://paste.org/index.php?id=1871)

There's a function, "skel_read", no matter what the name is, because the struct hereafter specifies the relation:

```
static struct file_operations skel_fops = {
	.owner =	THIS_MODULE,
	.read =		skel_read,
	.write =	skel_write,
	.open =		skel_open,
	.release =	skel_release,
};
```

In this function, there's a calling "usb_bulk_msg" for BULK transfer. What I have to do if I need to work with CONTROL transfer? Overload function is acceptable? 

After I install this module, new files appear in /dev/../... or /sys/bus/usb/... By writing to one of these files, I can pass data to the USB device? I guess so but can't test now because the problem above.

Thanks for your help in advance.

---

### Post by geraldm on 2008-01-24
There is no function overloading in the module.
First it is necessary to understand USB.  A device has assigned endpoints.  Every device has a control endpoint.  A device may have bulk transfer endpoint(s).  Transfer of information to and from the device is done in Usb Request Block(s) or URBs.  The URBs have a specific format for that request.

You need to have permissions to access the device.  The permissions are in /proc/bus/usb/001/005  where 001 is the bus number and 005 refers to the device number on this bus.

The skel module is an example module.  That type of programming was  done for very specialized drivers.  After the libusb was created, the preferred way to access the device is through libusb.  There are example programs in that source package; the examples just get the information that is available from the kernel.  To get examples of modules that talk to their device, find the source in the kernel sources.

You may also need to find more information on communication with a device, particularily major and minor numbers.  The driver must provide a minor number, and advertize it to the user.  The advertisement is displayed to the log in the skel program, where it provides info "USB Skeleton device now attached to ..."

You have a bit of learning to do before you can be successful.  Good luck.

Gerald

---

