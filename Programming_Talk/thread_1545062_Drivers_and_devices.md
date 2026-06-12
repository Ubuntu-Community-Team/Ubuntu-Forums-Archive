---
title: "Drivers and devices"
date: 2010-08-03
forum: Programming Talk
---

### Post by xefix on 2010-08-03
Hi, everyone

I have a pretty broad question about how devices are identified and assigned drivers in Linux systems (I'm preparing for modifying driver code in the near future). For instance, I have a USB device with some device descriptors (bDeviceClass, bDeviceSubClass, bDeviceProtocol, etc.), which match the descriptors recognized by the driver that this device uses (you can look this information up on LKDDb). My question is on how the matching process is done. Is it coded into the source of the driver itself, somewhere in the kernel, or done entirely with the rules files used by UDEV? I've looked at UDEV's man pages, but they don't seem to specify this.

---

### Post by xb12x on 2010-08-03
The process is called device enumeration.

All modern PC busses such as PCI, support enumeration. Older busses such as ISA do not support enumeration so are called 'legacy' buses.

Each modern bus has a defined amount of address (slots) where a device can exist. Some devices are hardwired on the motherboard, some devices are plugged into an actual slot. During enumeration each busses addresses are checked to see if a device responds. A read of all FF's indicates an empty slot, anything else indicates a device of some sort. A device is then further queried to determine its type. It can be a device or a bridge to another bus, and so on. The entire bus-tree is enumerated. Each bus is numbered, starting from bus 0. Each device (or bridge) is numbered on the bus it was discovered on. So each discovered device has a known address: bus number, device number.

Each device has a set of configuration registers which contain information. For example, each PCI device has 'PCI configuration registers' which when read completely define the device (Vendor-ID, Device-ID, Device-class, etc, ~ 0x100 registers in all).

During boot-up, the BIOS enumerates the bus-tree and creates a structure of devices it found. This structure, and many other structures such as memory map, etc, are placed in memory (RAM) at known addresses the the O.S. can find once it is booted. The O.S. itself also enumerates devices.

The O.S. has its list of drivers that need to be loaded. Each driver has a header which contains information about the driver and its intended device: Bus-type, Vendor-ID, Device-ID, device class-type, etc. As the kernel attempts to load a driver during boot, the driver uses the kernel's device list to get the address of its device so it can access and initialize its device. If the driver cannot successfully initialize its device the driver reports failure to the kernel.

---

### Post by xefix on 2010-08-03
Thank you for your detailed answer. I have a follow-up question:

> Each driver has a header which contains information about the driver and its intended device: Bus-type, Vendor-ID, Device-ID, device class-type, etc.

Where is this driver header located? Is it somewhere in the driver's source code? I've looked at the source code of USBNET, for instance, and I can't seem to find these device identifiers...

EDIT: Never mind, found the usb_device_id struct that seems to take care of this.

I have another related question, though. Why could it be that the same device would be assigned one set of drivers by one distro (e.g. Ubuntu) by a different set of drivers by another distro (e.g. Fedora)?

---

### Post by xb12x on 2010-08-03
*Why could it be that the same device would be assigned one set of drivers by one distro (e.g. Ubuntu) by a different set of drivers by another distro (e.g. Fedora)?*

One guess is that the distros don't use the same version of the Linux kernel. Another guess is that you are looking at two different machines, therefore two different device-trees.

Drivers also exist in a tree, analogous to the device-tree.

There are many different classes of drivers. The root of the driver-tree corresponds to the root of the bus-tree. Each major branch of the bus-tree has a corresponding driver, and so on. A  leaf on the driver tree corresponds to a leaf on the bus-tee, which is probably a device driver for a device. Drivers communicate up and down the tree. Think of the root driver, talking to a network driver, talking to a protocol driver, talking to a bus driver, talking to an adapter driver, etc, etc.

I've given a very simplistic view of how all this fits together. It's much more complex.

---

### Post by xefix on 2010-08-03
The machine is the same but you're right, the two distros do use different kernel versions. Are you saying that these kernels could have different device trees? Or is the different driver assignment more about the way the device interfaces are read in from the device (if it has multiple interfaces)?

btw, thanks for your awesome responses. They are really helping me!

---

### Post by Bachstelze on 2010-08-03
There can be multiple drivers that exist for the same device.  For example for Atheros wifi adapters, you have the madwifi and ath5k drivers.  Obviousy, two drivers cannot be loaded at once for the same device, so when more than one driver is available, it is up to the distributor to choose which one they want to use in their distribution, usually by blacklisting the one they don't want (or leaving it out altogether).

---

### Post by xb12x on 2010-08-03
*Are you saying that these kernels could have different device trees?*

Yes they could. A major reason why new versions of the kernel are developed is to improve how system resources are used. Kernel changes often times require driver changes and vice-versa.

Also, the enumeration process itself can be different between kernel versions. The most obvious change to the process is the order of assignment of system resources to devices/drivers. System resources are Interrupts, I/O addresses, Memory addresses, DMA channels, etc. Resources are finite, limited. Hardware interrupts (IRQ's), for example, must usually be shared among devices. The order of device discovery and order of resource allocation might be affecting the differences between the distros that you are seeing.

*Or is the different driver assignment more about the way the device interfaces are read in from the device (if it has multiple interfaces)?*

My first guess is that has very little or nothing at all to do with the differences you are seeing. But that is definitely a guess on my part.

The answer to those questions depends on how far apart the kernel version are. The digits of the version number reflect the driver model required. Linux kernels 1.x had an _entirely_ different driver model than Linux kernels 2.x. And there are driver model differences in the subversions as well.

---

### Post by xefix on 2010-08-03
@Bachstelze

I don't believe that this is the case for my particular situation. I'll give more details on my device and drivers - I should've done that at the very start. 
I have a device that conforms to the RNDIS protocol (unfortunately). It works fine on windows; however, because it has a slightly non-standard USB RNDIS descriptors, it does not work with native Linux RNDIS drivers (rndis_host, I think). Using ndiswrapper and the windows drivers, I was able to get it to work on Fedora (13), but not on Ubuntu (Lucid), where cdc_acm claims the device instead of ndiswrapper. If I blacklist cdc_acm, no drivers (aside from generic USB 2.0 drivers - uhci_hcd, I think) get assigned to the device at all. My hope is that by modifying rndis_host or some other native driver, I'll be able to get the device to work without having to use ndiswrapper. I first want to understand why it's working so differently for the two distros, though.

---

### Post by xb12x on 2010-08-03
xefix,

I have a couple of questions:

Is your working Windows solution running on the same machine as your Linux?

Have you tried all the different USB ports? I'm thinking in terms of IRQ's available at the different ports for the different O.S.s 

IRQ's almost always need to be shared, which depends on how (order) they were allocated. Not all IRQ's can be shared. IRQ's assigned to legacy devices (serial ports, printer ports, floppy controllers) cannot be shared with IRQ's assigned to PCI, for example. Compare the list of IRQ usage from Windows to Lucid to Fedora. It's possible your problem lies there. This is why you might get lucky if you try all the available USB ports. 

Please keep us informed of your progress.

---

### Post by xefix on 2010-08-04
I have tried all the USB ports, but my Linux OSs and Windows are on different machines. I can try installing them on the same machine and testing the drivers then.

---

