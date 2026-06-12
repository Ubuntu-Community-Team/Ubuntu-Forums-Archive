---
title: "Connecting External Hard Drive"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by RussW210 on 2008-11-17
I just upgraded a week ago to Ubuntu 8.10 from Ubuntu 8.04.  My External Hard Drive was being picked up in 8.04 but it isn't even recognized anymore under 8.10.

My 250GB HD is connected via USB to the back of my computer.  In the "fstab" file it doesn't even show the hard drive as connected when turned on.

It doesn't show in my home folder either.  Any ideas?

---

### Post by RussW210 on 2008-11-17
More Information:

Since then my friend also plugged his external hard drive into my usb port (that sounds bad, especially being the only open hole - the back usb port... couldn't help myself).  Could that have something to do with mine is not now connecting?

He bought a Lacie d2 Quadra and had it connected to his Mac before plugging into my PC.

---

### Post by SuperSonic4 on 2008-11-17
Did your friends work in yours?/Does yours work in a different slot and/or pc

---

### Post by RussW210 on 2008-11-17
Yes, my friends worked in mine.  He brought it over yesterday.  I tried it in another slot and still nothing.  Let me try connecting to my laptop... one sec.

---

### Post by RussW210 on 2008-11-17
Yes, my 250gb external hard drive works on my Windows XP laptop.

---

### Post by RussW210 on 2008-11-17
When I type:

sudo mount -t ntfs-3g /dev/sda1 /media/sda1/ -o force

I get:

NTFS signature is missing.
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

---

### Post by RussW210 on 2008-11-17
Actually, sda1 is my /boot so that mount wouldn't work.  Still clueless as to how to get my External HD to mount.

---

### Post by gletob on 2008-11-17
post the output of 
```
fdisk -l
```

---

### Post by RussW210 on 2008-11-17
"sudo fdisk -l" returns to me:

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x60000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1867    14996646   83  Linux
/dev/sda2            1868        2614     6000277+  82  Linux swap / Solaris
/dev/sda3            2615       77825   604132357+   5  Extended
/dev/sda5            2615       62371   479998071   83  Linux
/dev/sda6           62372       67351    40001818+  83  Linux
/dev/sda7           67352       71086    30001356   83  Linux
/dev/sda8           71087       76066    40001818+  83  Linux
/dev/sda9           76067       77825    14129136   83  Linux


Looks like my internal hard drive... though /dev/sda3 is not on my "fstab" file.  And that is a lot of blocks.  Don't think that could be my external hard drive though because my external is only 250gb.

---

### Post by gletob on 2008-11-17
Did you have the external drive plugged in when doing that?

---

### Post by RussW210 on 2008-11-17
Yes, my external is plugged into my back port.  The same one my friend had his connected to (which worked).  It is also turned on.

---

### Post by RussW210 on 2008-11-17
I turn off the External Hard Drive and then try sudo fdisk -l again and everything remains the same.  It's like it isn't even recognizing it.

---

### Post by gletob on 2008-11-17
plug the drive in, turn it on, and run the command: 
```
lsusb
```
and post the output

---

### Post by RussW210 on 2008-11-17
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 010: ID 0000:0000  
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 004: ID 413c:2105 Dell Computer Corp. 
Bus 003 Device 002: ID 046d:c01e Logitech, Inc. MX518 Optical Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by RussW210 on 2008-11-17
My friend told me to try "mkdir /mnt/usbdrive" as root.  I did that.  Now I did "sudo mount -t vfat /dev/sda1 /mnt/usbdrive" and it gave me the following response:

mount: /dev/sda1 already mounted or /mnt/usbdrive busy
mount: according to mtab, /dev/sda1 is mounted on /boot

---

