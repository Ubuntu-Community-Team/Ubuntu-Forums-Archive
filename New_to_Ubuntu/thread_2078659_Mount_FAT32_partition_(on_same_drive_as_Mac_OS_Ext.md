---
title: "Mount FAT32 partition (on same drive as Mac OS Ext. partition)"
date: 2012-10-31
forum: New to Ubuntu
---

### Post by Roevardottir on 2012-10-31
Hi everybody, 

I hope this hasn't already been asked a hundred times. 

So I have an external hard drive that has three partitions on it, two Mac OS Extended (Journaled) and one FAT32. I'm unable to mount the FAT-partition on Ubuntu. I thought it might be because it was created on a Mac, so I re-formatted that partition on a PC, to no avail.
 All other FAT32-devices mount fine on Ubuntu, and this particular one is fine on Windows and Mac. 
So I figured Ubuntu probably doesn't like the OS Ext. partitions on the same drive.

Is there any way I can mount the FAT-partition anyway? I can't reformat the OS Extended partitions, and I'd obviously prefer to not have to buy another drive to back up stuff from the Ubuntu system. 

This is the answer to a sudo fdisk -lu command, if that helps:

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xa44e69f2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   926808063   463300608    7  HPFS/NTFS/exFAT
/dev/sda3       926808064   976773119    24982528   27  Hidden NTFS WinRE

```None of that is the external drive, right? Does that mean it's not even seeing it?

Any help would be much appreciated! Thanks heaps!

---

### Post by Lars Noodén on 2012-10-31
FAT won't work for backing up Linux partitions unless you are making a tarball.  It can't handle the basic file permissions and ownerships.

---

### Post by Roevardottir on 2012-10-31
Thank you. Fair enough, but in order to reformat it I need to get Ubuntu to see it - how do I do that?

---

### Post by jwbrase on 2012-10-31
Please post the output of:

```
ls /dev | grep sd
```

It looks to me like Ubuntu may not be seeing the external drive at all.

---

### Post by Roevardottir on 2012-11-01
Edit: Sorry, ignore this, will post the outcome later.

---

### Post by Roevardottir on 2012-11-01
Alright, here we go - (with the drive actually attached, this time - silly me ;))

The outcome of ls /dev | grep sd:

```
sda
sda1
sda2
sda3
```

---

### Post by kanikilu on 2012-11-01
After plugging it in, do you see anything related in ```
dmesg | tail
``` What do you get from ```
lsusb
``` ?

I'm assuming here that it's USB, is that right?

You may want to also look at some of the other troubleshooting steps:

[https://help.ubuntu.com/community/Mount/USB#Troubleshooting](https://help.ubuntu.com/community/Mount/USB#Troubleshooting)

// Edit - you mentioned that the external drive has 3 partitions on it, but apparently so does the one that is being seen (sda). So your internal 500GB drive also has 3 partitions on it? Just trying to clarify what devices you have and how they're setup...

---

### Post by Roevardottir on 2012-11-01
The outcome of dmesg | tail (yes, it's a USB-drive)

```
[ 4649.274773] usb 4-1: >Device not responding to set address.
[ 4649.478400] usb 4-1: >Device not responding to set address.
[ 4649.682113] usb 4-1: >device not accepting address 4, error -71
[ 4649.794104] usb 4-1: >Device not responding to set address.
[ 4649.997803] usb 4-1: >Device not responding to set address.
[ 4650.201519] usb 4-1: >device not accepting address 5, error -71
[ 4650.313351] usb 4-1: >Device not responding to set address.
[ 4650.517165] usb 4-1: >Device not responding to set address.
[ 4650.720821] usb 4-1: >device not accepting address 6, error -71
[ 4650.720843] hub 4-0:1.0: >unable to enumerate USB device on port 1
```Looks like it's seeing something, but clearly not liking it...

And lsubs:

```
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 0cf3:3004 Atheros Communications, Inc. 
Bus 001 Device 004: ID 2232:1028 
```Yes, the internal drive has three partitions on it (created a small second one to run Ubuntu next to Windows, in the process of which a tiny third one also seems to somehow have happened... ;))

BTW, when I say I can't reformat the OS Ext partitions: Of course I can reformat the entire drive, I just need an OS Ext partition back in the end. I'd prefer not to, obviously, but if it helps...

Thanks for all your help so far!

Edit: Thanks for the troubleshooting link, I'll have a look through it!

---

### Post by kanikilu on 2012-11-01
Sorry this probably doesn't help much, but I actually had a similar problem a couple months ago ("unable to enumerate USB device"), and I was never able to figure it out. A google search brings up a lot of discussion on the topic, but apparently no "quick fix" :(

A common suggestion is to simply try a different USB port, preferrably not on a hub.

Good luck...

---

### Post by Roevardottir on 2012-11-03
It does help - saves me spending any more time looking for a solution that doesn't exist. I'll try to format the entire thing to FAT32 on Windows, then re-format and partition it on Ubuntu (if it can read it, that is), then create an OS Ext partition. See if that works. 

Will have to wait a few days to do that though - I'll post how it went, in case anybody ever runs into a similar problem. 

Thanks for the help!!!

---

