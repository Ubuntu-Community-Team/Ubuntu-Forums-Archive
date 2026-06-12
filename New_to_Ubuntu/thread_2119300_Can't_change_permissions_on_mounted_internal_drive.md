---
title: "Can't change permissions on mounted internal drive"
date: 2013-02-23
forum: New to Ubuntu
---

### Post by koa4evr on 2013-02-23
I am pretty new with Linux and i need some help with permissions Ubuntu 11.10. I have searched for hours trying to find a solution. I have a mounted internal hard drive and cannot change permissions on it. i have set shares on it and can see it from my windows devices and through the installed serviio from other dlna devices.  When i try to change permissions on the mount point it just doesn't, no errors though.
From the GUI i can change the permissions in the drop down boxes but then changes automatically back to no access.
From command line using chmod -R 777 '/media/MEDIA STUFF' it allows me through with no errors like it did it, but ls -l shows permissions did not change.
It is a vfat drive.
Any help?

---

### Post by schragge on 2013-02-23
Changing Unix file permissions with *chmod* makes little sense on a vfat volume. How do you mount it? Through /etc/fstab? Then you can set mount options *fmask* and/or *dmask* there.

---

### Post by sandyd on 2013-02-23
Moved to Absolute Beginners Section

---

### Post by koa4evr on 2013-02-23
i mount the drive manually so there is no fstab instance. how do i change permissions without chmod? i am the owner of the directory.

---

### Post by schragge on 2013-02-23
```

sudo mount -t vfat -o umask=000 /dev/[color=blue]sdb1[/color] /mnt

```Use your device name instead of [color=blue]sdb1[/color].

---

### Post by fdrake on 2013-02-23
install parted 
```

sudo apt-get install parted

```

can you post the output of 
```

sudo parted -l
less /etc/fstab

```

---

### Post by koa4evr on 2013-02-24
> **fdrake said:**
> install parted 
```

sudo apt-get install parted

```

can you post the output of 
```

sudo parted -l
less /etc/fstab

```
media@media:~$ sudo parted -l
sudo: /var/lib/sudo writable by non-owner (040733), should be mode 0700
[sudo] password for media: 
Model: ATA WDC WD400BB-00DE (scsi)
Disk /dev/sda: 40.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  39.0GB  39.0GB  primary   ext4            boot
 2      39.0GB  40.0GB  1063MB  extended
 5      39.0GB  40.0GB  1063MB  logical   linux-swap(v1)


Model: ATA WDC WD10EADS-11M (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start  End  Size  Type  File system  Flags


Model: ATA WDC WD10EACS-00D (scsi)
Disk /dev/sdc: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End     Size   Type      File system  Flags
 4      100GB  1000GB  900GB  extended
 5      100GB  1000GB  900GB  logical   ntfs


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label


# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=c311ad65-737f-41e4-ad24-8ead2f608b68 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=5426affb-0a7b-4647-8276-fa58de1147cc none            swap    sw              0       0

---

