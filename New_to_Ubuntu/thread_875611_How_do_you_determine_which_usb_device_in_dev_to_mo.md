---
title: "How do you determine which usb device in /dev to mount?"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by okos on 2008-07-31
Hi,
I am not sure if I am asking the question right.

There is probably 100 devices listed in /dev.
How do I decide which is the device I am looking for?

For example to mount my usb external hdd
mount /dev/sdb5 /media/disk

Well I knew it was /dev/sdb5 because the icon popped up and auto mounted.

Well if I did not look up the properties>meta info I would have never known which device to mount.

lsusb produces the following results:
> Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 003: ID 03f0:3f11 Hewlett-Packard PSC-1315/PSC-1317
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 006: ID 1058:1102 Western Digital Technologies, Inc.
Bus 001 Device 005: ID 047d:1023 Kensington
Bus 001 Device 004: ID 0451:2046 Texas Instruments, Inc. TUSB2046 Hub
Bus 001 Device 001: ID 0000:0000

To make things a little more confusing, why do I not mount the external hdd as such:
mount /dev/usbdev1.6_ep00 /media/disk  
Why is the device /dev/sdb5 and not /dev/usbdev1.6_ep00 ?

So rephrase my question, how do you determine which device in the /dev list when mounting a usb device?

---

### Post by mcduck on 2008-07-31
You are not mounting the device, you are mounting the partition on that device. ;)

Anyway, to find out the device you can either run "sudo fdisk -l" to list all drives & partitions, and find the one with correct size & file system.

Or run "tail -f /var/log/messages" and then plug the drive in, you'll see which name the partition will get (as well as all the other information about the device).

---

### Post by InfinityCircuit on 2008-07-31
Also, unless you built your ubuntu system from debootstrap and produced /dev with makedev GENERIC, /dev will only be populated with /dev/sdX and /dev/hdX when you plug in devices.

---

