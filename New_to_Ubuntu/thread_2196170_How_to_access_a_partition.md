---
title: "How to access a partition"
date: 2013-12-28
forum: New to Ubuntu
---

### Post by alastair2 on 2013-12-28
I've found it useful in Windows to keep my user documents in a separate partition from the main OS, so when I installed Ubuntu 12.04 as a clean install (ie not dual boot) I set up one partition for Ubuntu, another for swap space as required and a third one for my user documents.

However, I can't seem to access this final partition. I can see it when I go into Disc Maintenance but that's all.

It's possible that I didn't make it the correct type - anyone got any ideas?

Alastair

---

### Post by philinux on 2013-12-28
Open a terminal.

```
sudo fdisk -l
```

Post back what it reports.

---

### Post by alastair2 on 2013-12-28
```

alastair@Backup:~$ sudo fdisk -1
[sudo] password for alastair: 
fdisk: invalid option -- '1'
Usage:
 fdisk [options] <disk>    change partition table
 fdisk [options] -l <disk> list partition table(s)
 fdisk -s <partition>      give partition size(s) in blocks

Options:
 -b <size>             sector size (512, 1024, 2048 or 4096)
 -c[=<mode>]           compatible mode: 'dos' or 'nondos' (default)
 -h                    print this help text
 -u[=<unit>]           display units: 'cylinders' or 'sectors' (default)
 -v                    print program version
 -C <number>           specify the number of cylinders
 -H <number>           specify the number of heads
 -S <number>           specify the number of sectors per track

alastair@Backup:~$ ^C
alastair@Backup:~$
```

---

### Post by Mark Phelps on 2013-12-28
> sudo fdisk -lUse a lowercase L, not a one, for the parameter.

Besides, if you can see the partition in Disk Maintenance, then simply mount it from there.

---

### Post by alastair2 on 2013-12-28
Oops, sorry about that, let's try again:
```

alastair@Backup:~$ sudo fdisk -l
[sudo] password for alastair: 

Disk /dev/sda: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb3e0b3e0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    51199154    25599546   83  Linux
/dev/sda2        51199998   160086015    54443009    5  Extended
/dev/sda5        51200000    55105535     1952768   82  Linux swap / Solaris
/dev/sda6        55107584   160086015    52489216   83  Linux
alastair@Backup:~$
```

---

### Post by Morbius1 on 2013-12-28
> ... so when I installed Ubuntu 12.04 as a clean install (ie not dual boot) I  set up one partition for Ubuntu, another for swap space as required and  a third one for my user documents.
If you did that during the initial install of the OS it should be automounting at boot.

Please post the output of the following commands:
```
cat /etc/fstab
```
```
sudo blkid -c /dev/null
```
```
mount
```

---

### Post by whitesmith on 2013-12-28
> **alastair2 said:**
> I've found it useful in Windows to keep my user documents in a separate partition from the main OS, so when I installed Ubuntu 12.04 as a clean install (ie not dual boot) I set up one partition for Ubuntu, another for swap space as required and a third one for my user documents.Generally people who want this kind of setup--I'm one of them--will install Ubuntu with root (/) as one partition and ~ as another. Swap may not need a partition at all, depending on available RAM. I have 32GB, so any amount of swap space would be wasted because it would never be touched by the system.

---

### Post by alastair2 on 2013-12-30
Morbius1 - here are the results:

alastair@Backup:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=01029a47-987c-4a89-8b0e-e04d1eb1fc9b /               ext4    errors=remount-ro 0       1
# /usr/local was on /dev/sda6 during installation
UUID=5b091541-deef-4373-a927-7e1598142776 /usr/local      ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=5dac3551-da8f-4806-ba69-e840e7216093 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
alastair@Backup:~$ 

alastair@Backup:~$ sudo blkid -c /dev/null
[sudo] password for alastair: 
/dev/sda1: UUID="01029a47-987c-4a89-8b0e-e04d1eb1fc9b" TYPE="ext4" 
/dev/sda5: UUID="5dac3551-da8f-4806-ba69-e840e7216093" TYPE="swap" 
/dev/sda6: LABEL="Macfadyen files" UUID="5b091541-deef-4373-a927-7e1598142776" TYPE="ext4" 
alastair@Backup:~$ 


alastair@Backup:~$ mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
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
/dev/sda6 on /usr/local type ext4 (rw)
gvfs-fuse-daemon on /home/alastair/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=alastair)
alastair@Backup:~$ 

Regarding the business of mounting the partition, according to Disk Utility, the partition is mounted at /usr/local

Thanks to all for your help.

---

### Post by Morbius1 on 2013-12-30
>  Regarding the business of mounting the partition, according to Disk Utility, the partition is mounted at /usr/local
Indeed it is:
>  UUID=5b091541-deef-4373-a927-7e1598142776 /usr/local      ext4    defaults        0       2
So are you saying you can't access it? If you run the following command do you not see anything show up in Nautilus:
```
nautilus /usr/local
```

---

### Post by alastair2 on 2013-12-30
Yes, I get the usual screen coming up with a number of directories such as bin, etc, games and so on.

In fact since I made the last post, I've actually managed to find my way to usr/local (whilst trying to save a word processed document), but when I tried to create a top level directory for my user files I was refused permission to do so. I feel I'm getting closer, but Ubuntu clearly isn't going to yield its secrets willingly :-(

---

### Post by Morbius1 on 2013-12-30
> **alastair2 said:**
> Yes, I get the usual screen coming up with a number of directories such as bin, etc, games and so on.

In fact since I made the last post, I've actually managed to find my way to usr/local (whilst trying to save a word processed document), but when I tried to create a top level directory for my user files I was refused permission to do so. I feel I'm getting closer, but Ubuntu clearly isn't going to yield its secrets willingly :-(
Um ... /usr/local is part of the operating systems file stucture and as such is owned by root not you. Others can read the contents of this folder but only root can write to it and that is by design.

Changing permissions to allow you or any other user write access to that folder is not a good idea. If you wanted a "data" partition so you could keep your own personal files separate from the operating system files having it mount to /usr/local was not a good idea.

---

### Post by 3rdalbum on 2013-12-30
/usr/local is really not a good place to mount a "documents" partition. Typically, you would mount it at /home so it automatically is used for your home directory.

For the moment, let's not change it to /home because it requires a few steps that might be beyond your safe abilities. However we can make it so it is not mounted by default, and you just click it once to mount it.

```
gksudo gedit /etc/fstab
```

Put a # symbol at the start of the line that refers to /usr/local to disable the line. That is, the start of the WHOLE line, so the # is the very first thing on that line. Save your changes and reboot. Your /dev/sda6 partition will be visible on the left side of the screen. Click it to mount it.

---

### Post by alastair2 on 2013-12-31
3rd album

I've entered the code that you showed above and there is already a # at the start of the line including /usr/local

I'm beginning to wonder if I should just reinstall ubuntu without this extra partition - it seemed a good idea but the reality has produced results that I didn't expect!

---

