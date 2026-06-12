---
title: "Missing Partition"
date: 2011-11-01
forum: New to Ubuntu
---

### Post by drklunk on 2011-11-01
Alright, I upgraded to 11.10 from 10.04 using the system update manager. I unmounted my storage partition containing only media and office files, no programs and nothing installed. Now I cannot find where the partition is, its as if the OS doesnt even recognize its there. 

The partition use to be stored in /media but now doesnt even show up in System Check>File Systems.

How do I go about mounting the missing partition?

---

### Post by coffeecat on 2011-11-01
Let's get some information about your system. Open a terminal and post the output of these commands:

```
sudo fdisk -lu
sudo blkid
mount
ls -l /media
cat /etc/fstab
```

You can highlight the output to right-click and copy in order to be able to paste into your post. Please enclose the output between [noparse]```
 and 
```[/noparse] tags.

By the way, upgrading to 11.10 from 10.04 would have involved intermediate hops via 10.10 and 11.04. Is this what you did?

---

### Post by drklunk on 2011-11-01
Yes, I went from 10.04>10.10>11.04>11.10. I never checked during any of the upgrades to see if I could still access the partition. In the lines you had me run you can see the partition Im trying to access labeled sda4

```


william@HAL:~$ sudo fdisk -lu
[sudo] password for william: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x57b657b6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2046       10239        4097    5  Extended
/dev/sda2           10240   157571071    78780416   83  Linux
/dev/sda4       157571072   976769023   409598976    7  HPFS/NTFS/exFAT
/dev/sda5            2048       10239        4096   82  Linux swap / Solaris
william@HAL:~$ sudo blkid
/dev/sda2: UUID="6fb68f8e-9cf2-4369-aa94-c4a404b11269" TYPE="ext4" 
/dev/sda4: UUID="948C12A38C127FC2" TYPE="ntfs" 
/dev/sda5: UUID="0c6a302a-5301-434a-bd88-29939c84a3c1" TYPE="swap" 
william@HAL:~$ mount
/dev/sda2 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/william/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=william)
william@HAL:~$ ls -l /media
total 0
william@HAL:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=6fb68f8e-9cf2-4369-aa94-c4a404b11269 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=0c6a302a-5301-434a-bd88-29939c84a3c1 none            swap    sw              0       0

```

---

### Post by coffeecat on 2011-11-01
First thing. Open Software Centre or Synaptic and check to see that the package ntfs-3g is installed. Some people are reporting that it disappears during the upgrade. This didn't happen to me with two upgrades, but enough people are reporting it to suggest there might be an upgrade bug. If it's not installed, install it. Don't try to install ntfsprogs - this now conflicts with ntfs-3g in Oneiric.

Now open a Nautilus windows by clicking on the home icon in the launcher. In the left pane, do you see the NTFS partition? Since it doesn't have a partition label, it will probably say something like 420 GB File System. If it's there, try clicking on it.

---

### Post by drklunk on 2011-11-02
I checked to see if the package was installed, saw it was, then opened the home folder. I didnt understand what you meant by the left pane, think I know what youre talking about but mine doesnt show it. Ended up poking around the menu bar, saw "Computer" in places, opened it, bingo there it was.

I really appreciate the help man, led me right to it =)

---

### Post by coffeecat on 2011-11-02
> **drklunk said:**
> I didnt understand what you meant by the left pane,

A pane is part of a window. Have a look at a window in a house. If the window is divided into several sections of glass, those are panes. 

[http://en.wikipedia.org/wiki/Paned_window](http://en.wikipedia.org/wiki/Paned_window)

As for a real window, so for a computer GUI window. :) See my screenshot. The left pane in mine has several partitions under "Devices". Yours will have fewer.

Anyway, glad you found it.

---

### Post by drklunk on 2011-11-02
Much fewer xD. I had the right idea then, how did you get that to show up? Whenever I set mine up for an extra pane it defaults to the folder or drive Im in. Yours looks to be the tree style so to speak

---

### Post by coffeecat on 2011-11-02
> **drklunk said:**
>  Yours looks to be the tree style so to speak

No. mine is the default Places view. If you've upgraded, yours may be showing a different view depending on what you set in an earlier release. Go to the Nautilus View menu in the panel -> Sidebar. You have a choice of Tree or Places.

I notice they call it "sidebar" so apologies for confusing you with "pane". But "pane" is a common metaphor used when referring to parts of GUI windows.

---

### Post by drklunk on 2011-11-02
Good deal, got it all set up. I always liked having that there, makes everything faster. Thanks again for the help!

---

