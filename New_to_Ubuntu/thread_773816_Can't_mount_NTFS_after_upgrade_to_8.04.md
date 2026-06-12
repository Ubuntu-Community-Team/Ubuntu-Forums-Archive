---
title: "Can't mount NTFS after upgrade to 8.04"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by Marcs316 on 2008-04-29
I just upgraded to Ubuntu 8.04 Hardy Heron and I can no longer mount my NTFS drive. It used to show up in the file explorer as "197GB Filesystem" or something similar, but is now showing up as "SCSI Drive" and will no longer mount. It also used to show up as something else after running fdisk, but now shows up as "/dev/sdb1".

It worked fine in Feisty Fawn and Gusty Gibbon, but now it just refuses to work. I also rebooted into the Windows partition a few times and shut it down correctly to make sure it wasn't conflicting with Ubuntu, but to no avail. I tried mounting it in the terminal and it says 

> ntfs-3g: Failed to access volume '/dev/sdb1': No such file or directory
Please type '/sbin/mount.ntfs-3g --help' for more information.

I could really use some help because I have no idea what the problem could be. 

Thanks.

---

### Post by Joeb454 on 2008-04-29
Can you try this from a terminal ```
sudo aptitude reinstall ntfs-3g
``` just to make sure your ntfs-3g install is ok :)

---

### Post by gklaus on 2008-04-29
I had the same problem of being unable to mount ntfs partitions after the upgrade to Hardy, found a solution and thought I should share it. Disclaimer: 1) I am on Kubuntu, so things may be a bit different here, 2) I am no specialist for Ubuntu or Linux, so my solution may not be the "correct" or most elegant one.

Problem:
After the upgrade different attempts to mount ntfs partitions resulted in some kind of "permissions denied" error. However, a manual mount attempt with 

sudo mount -a

resulted in this message:

/sbin/mount.ntfs-3g: /usr/local/lib/libfuse.so.2: version `FUSE_2.7' not found (required by /sbin/mount.ntfs-3g)

Solution:

Looking up /usr/local/lib/libfuse.so.2 revealed that this was just a link to libfuse.so.2.6.3 in the same directory. The package manager showed that the newest version, 2.7.2, of the library was installed in /lib/ instead of in /usr/local/lib.

So I updated the link:

as root

rename /usr/local/lib/libfuse.so.2 to libfuse.so.2.old

create a new link (right click, new link, link to URL) named libfuse.so.2.desktop to link to /lib/libfuse.so.2 which in turn is a link to /lib/libfuse.so.2.7.2, i.e. the new version.

In short: /usr/local/lib/libfuse.so.2 -> /lib/libfuse.so.2

Mounting ntfs partitions as user with write permission worked after that.

---

### Post by gn2 on 2008-04-29
Other options to try, add the ntfs-config utility or in Add/Remove, the Storage Device Manager.

---

### Post by Marcs316 on 2008-04-29
I reinstalled ntfs-3g, but the problem is still there. I also added Storage Device Manager and it sees my hard drive as "SCSI2". 

I don't know if this will help, but here is the result of my fdisk and mount attempts:

> cy-240@MDC-FF:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000bc9b9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38536   309540388+  83  Linux
/dev/sda2           38537       38913     3028252+   5  Extended
/dev/sda5           38537       38913     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8db447c6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       24791   199133676    7  HPFS/NTFS
cy-240@MDC-FF:~$ sudo mount /dev/sdb1 /media/windows
mount: special device /dev/sdb1 does not exist


You can clearly see that /dev/sdb1 is my NTFS partition, but when I try to mount it, it tells me that it doesn't exist. I put in my copy of Feisty Fawn that I had and ran it live. It quickly saw my NTFS partition and let me mount it without any problems.

---

### Post by Adrian1978 on 2008-04-30
i'm having exactly the same problem with mounting my ntfs hd? i have to Hd one is SATA and the other is SATAII, by any change is this your configuration?

---

### Post by artships on 2008-05-02
> **gklaus said:**
> 
sudo mount -a

resulted in this message:

/sbin/mount.ntfs-3g: /usr/local/lib/libfuse.so.2: version `FUSE_2.7' not found (required by /sbin/mount.ntfs-3g)

Solution:

In short: /usr/local/lib/libfuse.so.2 -> /lib/libfuse.so.2


That fixed it for me.  My specific steps were:

sudo aptitude reinstall ntfs-3g
sudo mv /usr/local/lib/libfuse.so.2 /usr/local/lib/libfuse.so.2.old
sudo ln -s /lib/libfuse.so.2.7.2 /usr/local/lib/libfuse.so.2
sudo rm .hal-mtab .hal-mtab-lock

Now my internal NTFS drives mount and so do my external ones when plugged-in.  Thank you, gklaus!

---

### Post by Marcs316 on 2008-05-04
Nothing's worked for me, yet. Does anyone else have any ideas how to fix the issue?

---

### Post by colin08 on 2008-05-07
I had same problem MY Solution

Go to System> Add/Remove
Find Storage Device Manager
Add This
Now you can see missing Drive 
Click arrow to see partitions
Select and Mount

Hope this helps
Colin08

---

### Post by Adrian1978 on 2008-05-07
storage device manager and gparted don't detect my hdd's. I see them with ubuntu 7.10 liveCD, i see them with win, but Hardy (Livecd and clean instalation) don't. fdisk doesn't detect them either. I don't now what to do,

---

### Post by Marcs316 on 2008-05-08
> **Adrian1978 said:**
> storage device manager and gparted don't detect my hdd's. I see them with ubuntu 7.10 liveCD, i see them with win, but Hardy (Livecd and clean instalation) don't. fdisk doesn't detect them either. I don't now what to do,

It's the exact same thing with me. I've still got no idea for a solution, either.

---

### Post by artships on 2008-05-11
Marcs and Adrian;  What is the output from:

sudo mount -a

And what does your /etc/fstab say about the drives?

---

### Post by StickyCube on 2008-05-11
I've got a similar, if not the same problem. One internal hd (with ext3 and ntfs partitions), one ntfs external connected by eSATA.  7.10 worked beautifully, in 8.04 the external one doesn't appear in /dev, as far as I can tell, and in /media/sda1 (where it used to mount), there is nothing.
sudo mount -a:
> ntfs-3g: Failed to access volume '/dev/disk/by-uuid/305821F55821BA8C': No such file or directory
Please type '/sbin/mount.ntfs-3g --help' for more information.

/etc/fstab:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb2
UUID=4570ca07-ef1b-47f5-aa71-a9d4f2a60789 /      ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=305821F55821BA8C /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb1
UUID=2AAAE208AAE1CFFD /media/sdb1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sdb3
UUID=fecd2588-e434-4d70-8c82-7c310a960834 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
usbfs         /proc/bus/usb usbfs   devgid=14,devmode=0660 0 0

for me, I have noticed that if I use the old version of the kernel from grub (sorry I don't remember the number...I assume it's from feisty), then this problem doesn't happen.  this is not a fix for me, however, because many things are slowed considerably, making it hard to use.

---

### Post by petoro on 2008-05-11
At last I have found a solution.

My C: NTFS disk had no volume name in Vista. Then it appeared in Ubuntu as something like: 132.2 GB disk.

This strange label "132.2 GB disk", perhaps for the dot in the middle, couldn't be added to the fstab list.

The utility ntfs-config couldn't recognize it either.

So I've loaded Vista, I've renamed the C: volume label from "nothing" to DiskC and then I have been able to configure the fstab properly with ntfs-config in Ubuntu 8.04.

(To install ntfs-config: sudo apt-get install ntfs-config
To run it: sudo ntfs-config)


Petoro

---

### Post by Adrian1978 on 2008-05-11
When i se sudo mount -a nothing happens because the hd i want to mount is not listed in the fstab and it's not listed in the /dev/idisk directory. i got the ntfs-3g error when i updated from 7.10, but then i decided t go on a clean installation of 8.04, in that point i never get the error again because 8.04 didn't detect the hd and with the clean install the new fstab didn{t have reference to the hd anymore. Thanks to all i realy apreciate your help with this

---

