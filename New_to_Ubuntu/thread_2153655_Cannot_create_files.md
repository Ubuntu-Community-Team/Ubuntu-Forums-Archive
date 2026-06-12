---
title: "Cannot create files"
date: 2013-06-11
forum: New to Ubuntu
---

### Post by marcerickson on 2013-06-11
I can't create files on the 1 TB RAID disk installed in my Ubuntu 12.04 box.

---

### Post by Moose on 2013-06-11
Some more information would have been helpful..

---

### Post by marcerickson on 2013-06-11
Tell me what you need and I'll provide.  I don't know where to start.

---

### Post by QIII on 2013-06-11
Hello!

Rather than having everyone else guess, it might be best for you to describe what you are doing, what sorts of files you are attempting to create and how you are attempting to create them.

Tell us what you are doing that is not working.  That'll make it easier for everyone to help.

Best wishes.

---

### Post by marcerickson on 2013-06-11
When I open the 1 TB Filesystem in Computer and right click to try to create a folder or document, they're greyed out.

---

### Post by deadflowr on 2013-06-11
deleted

---

### Post by marcerickson on 2013-06-11
When I open the 1 TB Filesystem in Computer and right click to try to create a folder or document, they're greyed out.

---

### Post by deadflowr on 2013-06-11
Oh.
So what you saying is that when you try to open the file manager and click on the 1TB selection you have, it won't let you create anything?

It's probably an ownership/permissions thing.

Is the 1TB a part of the system or is it something like an extra partition for storage?

---

### Post by marcerickson on 2013-06-11
You are correct about file manager.

Yes it probably is.

The 1 TB filesystem is 2 - 1 TB SATA drives in a RAID 1 array attached to a CERC RAID card.  Ubuntu 12.04 desktop is on a SATA drive attached directly to the motherboard.

---

### Post by marcerickson on 2013-06-17
I don't know where to go from here - help is requested.  Thanks.

---

### Post by coffeecat on 2013-06-17
> **marcerickson said:**
> The 1 TB filesystem is 2 - 1 TB SATA drives in a RAID 1 array attached to a CERC RAID card.  Ubuntu 12.04 desktop is on a SATA drive attached directly to the motherboard.

> **marcerickson said:**
> When I open the 1 TB Filesystem in Computer and right click to try to create a folder or document, they're greyed out.

I am surprised that someone who knows how to create a RAID array seems to be unaware of the information needed for others to help you. You are not helping yourself by being so sparse with your information. So...

I'm going to guess at the most important piece of information that you haven't given us - the actual type of filesystem. If the filesystem is a Linux one, say ext3 or ext4, it is probably owned by root at the moment - that would be one explanation for the greying out of the create folder/document choices in the context menu. If so, you simply need to own the filesystem. You can do this by running this terminal command, suitably modified:

```
sudo chown yourusername: /path/to/mountpoint
```

Substitute your login name for yourusername, don't forget the trailing colon after yourusername, and substitute the full path of the mountpoint of the mounted filesystem for /path/to/mountpoint.

---

### Post by marcerickson on 2013-06-17
I'm a Linux newbie - that's why I don't know what info you need to help.

That's great!  That's the first piece of the puzzle - I think the filesystem IS owned by root (it is ext3).

Now how do I find out where the volume is mounted?

---

### Post by coffeecat on 2013-06-17
> **marcerickson said:**
> 
Now how do I find out where the volume is mounted?

How did you mount it? From the file manager or have you set up a custom mount in /etc/fstab?

Whatever the answer, post the output of these two terminal commands and we can work that out:

```
sudo fdisk -lu
mount
```

You can copy the terminal output by highlighting with the mouse, right-clicking and choosing "Copy". You will then be able to paste the output into your post with ctrl-v. Please enclose the output between [noparse]```
 and 
```[/noparse] tags to preserve formatting and for clarity. The simplest way of doing this is to highlight the output in the message editor and then click on the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the message toolbar.

---

### Post by marcerickson on 2013-06-17
The volume is mounted with File Manager.

```
 sudo fdisk -lu
[sudo] password for <username>: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001338b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       80324       40131   de  Dell Utility
/dev/sda2   *       81920     1056767      487424   83  Linux
/dev/sda3         1058814   156299263    77620225    5  Extended
/dev/sda5         1058816     5056511     1998848   82  Linux swap / Solaris
/dev/sda6         5058560    34422783    14682112   83  Linux
/dev/sda7        34424832    91956059    28765614   83  Linux
/dev/sda8        91957248   156299263    32171008    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 1000.2 GB, 1000170192896 bytes
255 heads, 63 sectors/track, 121597 cylinders, total 1953457408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0000eda4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  1953456127   976727040   83  Linux
```

```
mount
/dev/sda6 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sda2 on /boot type ext4 (rw)
/dev/sda7 on /home type ext4 (rw)
gvfs-fuse-daemon on /home/marc/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=marc)
/dev/sdb1 on /media/32dcf03e-1373-4ca0-b868-ccc653b2ddb3 type ext3 (rw,nosuid,nodev,uhelper=udisks)
```

---

### Post by coffeecat on 2013-06-17
> **marcerickson said:**
> ```

Disk /dev/sdb: 1000.2 GB, 1000170192896 bytes
255 heads, 63 sectors/track, 121597 cylinders, total 1953457408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0000eda4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  1953456127   976727040   83  Linux
```

Your 1TB filesystem is on partition /dev/sdb1, and...

> **marcerickson said:**
> ```
/dev/sdb1 on /media/32dcf03e-1373-4ca0-b868-ccc653b2ddb3 type ext3 (rw,nosuid,nodev,uhelper=udisks)
```

... is mounted on /media/32dcf03e-1373-4ca0-b868-ccc653b2ddb3.

The command you need is:

```
 sudo chown yourusername: /media/32dcf03e-1373-4ca0-b868-ccc653b2ddb3
```

Again - substitute your account login name for yourusername. I suggest you copy and paste the /media/32dcf03e-1373-4ca0-b868-ccc653b2ddb3 part to avoid typos. The reason that is so complicated is that you do not have a partition label, and in the absence of a label, the file manager automounts on a mountpoint named with the UUID of the partition. Hence the long alphanumeric string. If you were to name your sdb1 partition Data (for example), then the file manager would create the mountpoint /media/Data which can be more convenient, if only because "Data" would then show up in the left pane of the file manager rather than "1TB filesystem" or whatever is showing up. You can label the partition with Gparted or Disk Utility.

---

### Post by marcerickson on 2013-06-17
FANTASTIC! Issue solved!

I took your suggestion and changed the volume's label to data to make it easier for me in the future.

Thank you very much!

One down, a couple more to go...  ;-)

---

### Post by coffeecat on 2013-06-17
Good luck! :)

By the way, it would be useful to mark your thread as solved. Here's how:

[http://ubuntuforums.org/showthread.php?t=2121377](http://ubuntuforums.org/showthread.php?t=2121377)

---

