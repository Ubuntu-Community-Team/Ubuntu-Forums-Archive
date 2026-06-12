---
title: "External drive problem, just checking so I don`t mess things up (again))"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by nothingspecial on 2008-11-28
I have an external drive. During the course of the night it has disappeared from my filesystem completely.

Her is lsusb


```
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 03f0:8704 Hewlett-Packard 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 005: ID 0461:4d03 Primax Electronics, Ltd Kensington Mouse-in-a-box
Bus 003 Device 004: ID 046e:5808 Behavior Tech. Computer Corp. 
Bus 003 Device 003: ID 046d:08da Logitech, Inc. QuickCam Messanger
Bus 003 Device 002: ID 046e:5908 Behavior Tech. Computer Corp. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 0d49:7310 Maxtor 
Bus 001 Device 001: ID 0000:0000  
```

It is a Maxtor but it`s not that Maxtor. Here is fdisk -l
```

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf6edfd38

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14216   114189988+  83  Linux
/dev/sda2           14217       14593     3028252+   5  Extended
/dev/sda5           14217       14593     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1c937cb9

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60802   488384512   83  Linux
```

It is also a 500 gig formatted ext3 but like before that`s the other one showing.

Here`s a little bit of dmesg```

[  107.997056] EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
[  108.002609] EXT3 FS on sdb1, internal journal
[  108.002623] EXT3-fs: mounted filesystem with ordered data mode.
[  108.623137] UDF-fs: Partition marked readonly; forcing readonly mount
[  108.670947] UDF-fs INFO UDF 0.9.8.1 (2004/29/09) Mounting volume 'NEIL_YOUNG', timestamp 2003/07/28 19:42 (1000)
[  272.114023] usb 1-1: new high speed USB device using ehci_hcd and address 73
[  273.351760] usb 1-1: new high speed USB device using ehci_hcd and address 79
[  274.589496] usb 1-1: new high speed USB device using ehci_hcd and address 85
[  274.888954] usb 1-1: new high speed USB device using ehci_hcd and address 86
[  275.380051] usb 1-1: new high speed USB device using ehci_hcd and address 88
[  275.679559] usb 1-1: new high speed USB device using ehci_hcd and address 89
[  275.982961] usb 1-1: new high speed USB device using ehci_hcd and address 90
[  400.012267] usb 1-1: new high speed USB device using ehci_hcd and address 96
[  401.442659] usb 1-1: new high speed USB device using ehci_hcd and address 103
[  402.491735] usb 1-1: new high speed USB device using ehci_hcd and address 108
[  402.791191] usb 1-1: new high speed USB device using ehci_hcd and address 109
[  403.090641] usb 1-1: new high speed USB device using ehci_hcd and address 110
[ 1112.669814] usb 1-1: new high speed USB device using ehci_hcd and address 112
[ 1112.969332] usb 1-1: new high speed USB device using ehci_hcd and address 113
[ 1113.453404] usb 1-1: new high speed USB device using ehci_hcd and address 115
[ 1113.939499] usb 1-1: new high speed USB device using ehci_hcd and address 117
[ 1114.238947] usb 1-1: new high speed USB device using ehci_hcd and address 118
[ 1114.538398] usb 1-1: new high speed USB device using ehci_hcd and address 119
```

It seems it is trying to mount the drive and failing. Also at the top of the bit I`ve posted it says
```

EXT3-fs warning: maximal mount count reached, running e2fsck is recommended
``` But I think thats referring to the other one as in the next line it mentions sdb1.

There is no data loss (I hope) because it automounts as you would expect on my laptop.

Anyone know what`s up here.

And just so I didn`t look stupid I have tried swapping the usb ports over but to no avail.

Thanks.

---

### Post by meborc on 2008-11-28
it looks like you have an external in /dev/sdb1

what happens if you remove and insert it again?

---

### Post by nothingspecial on 2008-11-28
Thanks for replying. I have 2 externals /dev/sdb1 is the other one.

As to what happens if I plug it back in again the answer is nothing.

---

