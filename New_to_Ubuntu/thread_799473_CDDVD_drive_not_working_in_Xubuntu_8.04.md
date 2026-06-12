---
title: "CD/DVD drive not working in Xubuntu 8.04"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by bulldoze on 2008-05-19
I thought I had a good build on my laptop, everything worked fine until I tried to put a cd in the drive! I got a error message

Failed to mount "UDF Volume".
mount: block device /dev/scd0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so.

Anybody got any idea? Many thanks!

---

### Post by bulldoze on 2008-05-19
bump

---

### Post by bulldoze on 2008-05-19
Anyone?  .. Please?

---

### Post by bulldoze on 2008-05-21
I am still stuck on this one people! I have tried to search forums for an answer but no luck - I am betting this is a real easy problem as well!

---

### Post by Maestro23 on 2008-05-21
Looks like it doesn't like the file system. What is on the disc?

---

### Post by webmonster on 2008-05-21
bump

---

### Post by bulldoze on 2008-05-21
Just pictures. I will try with a disk burned from another pc. Thanks for the reply!

---

### Post by bulldoze on 2008-05-21
Ok I got to the bottom of it - disks burned by a particular PC do not work! 

I guess I should have worked this one out for myself but thanks for the help!

---

### Post by bulldoze on 2008-05-21
Hmmm actually this is still a problem - most disks are recognized by the system but when I eject I get this message:

Failed to eject

umount: /dev/scd0: not mounted
umount: /dev/scd0: not mounted
eject: unmount of `/media/cdrom0' failed.

although it does eject the disk!

and when I put the disk in again I get this message:

Failed to mount

mount: block device /dev/scd0 is write-protected, mounting read-only
mount: /dev/scd0 already mounted or /media/cdrom0 busy
mount: according to mtab, /dev/scd0 is already mounted on /media/cdrom0.

although the disk does work and I can view files with the file manager!

Anyone?

---

### Post by bulldoze on 2008-05-22
bump

---

### Post by aurous on 2008-07-15
I'm getting this message also on some of my burnt cd's. I burnt them while in windows vista. However I can take the cd's to another pc and they are readable. :(

---

### Post by aurous on 2008-07-15
I guess its a problem with the way that windows vista burns cd/dvd's. I was able to use vmware to read the discs.

---

### Post by mc4man on 2008-07-16
if you use vista to burn for compatibility use the 'mastering mode'. The default mode will only work on vista and maybe xp if fully updated

---

### Post by slitherthing on 2008-08-02
Hi there!

I'm having a problem similar to this one, and thought it might be best to post it here instead of starting a new thread. I'm using Xubuntu Hardy and my problem is that when I insert a disc into my dvd/rw drive, it will mount, but then throws the following error message:

> 
Failed to mount "Disc_Name"

mount: block device /dev/scd0 is write-protected, mounting read-only
mount: /dev/scd0 already mounted or /media/cdrom0 busy
mount: according to mtab, /dev/scd0 is already mounted on /media/cdrom0.



It kinda looks like its trying to mount the disc more than once, but I'm not too sure.

This is what my /etc/fstab looks like:

> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=3098842c-c3b1-470f-9f1d-efaa0e094299 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=9464e879-d2f8-4245-8dbe-4f169a62e0b9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   auto user,noauto,exec,utf8 0       0


Based on what I have seen in other threads, here is more information that may be pertinent:

Output of "lshw -C disk:"

> 
  *-cdrom                 
       description: DVD writer
       product: DVDRW SHW-160P6S
       vendor: LITE-ON
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/dvd
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /media/cdrom0
       version: PS09
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,relatime state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom
          logical name: /media/cdrom0
          configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,relatime state=mounted


Contents of /etc/mtab

> 
/dev/sda1 / ext3 rw,relatime,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.24-19-generic/volatile tmpfs rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
/dev/scd0 /media/cdrom0 udf ro,nosuid,nodev,utf8,user=username 0 0


The user from the mtab isn't "username," I've merely redacted it for privacy's sake.

I also get an error on eject:
> 
Failed to eject "Disc_Name."

umount: /dev/scd0: not mounted
umount: /dev/scd0: not mounted
eject: unmount of `/media/cdrom0' failed.


However, just like on insertion, the disc ejects with no other problems.

In the removable drives settings app, I can untick all of the automount options and the error on insert will go away. However, if I then mount the drive, or play the disc in totem or whatever, and then eject it, I still see the eject error. I've fiddled around with /etc/fstab a little bit, but I'm hesitant to do anything more drastic without some advice from someone a little more knowledgeable. Anyone have any suggestions? Thanks, and sorry for the length of this, but hopefully there's enough information that there's something useful in it.

---

