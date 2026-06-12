---
title: "Auto Mounting"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by spookyct on 2008-06-28
Hey guys,

I have to re-mount all of my drives everytime I start up.  Can someone help?

```
james@james-desktop:~/Documents$ sudo fdisk -l
[sudo] password for james: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00066e73

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6079    48829536   83  Linux
/dev/sda2            6080        6203      996030   82  Linux swap / Solaris
/dev/sda3            6204       20253   112856625    7  HPFS/NTFS
/dev/sda4           20254       28412    65537167+  83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1371d154

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2        3347    26876745    f  W95 Ext'd (LBA)
/dev/sdb2   *        3348       19457   129403575    7  HPFS/NTFS
/dev/sdb5               2        3347    26876713+   7  HPFS/NTFS

```

Here is my fstab file...


```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=4e62204a-eca5-4442-8f06-6bd40a8940b1 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=f372f85f-e8fc-4c3c-82ae-f8fb02397f90 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

Thanks for the help...

---

### Post by drs305 on 2008-06-28
Your NTFS partitions aren't listed in fstab, and thus not automatically mounted on boot. There is a new system called gvfs that doesn't automatically mount NTFS systems on boot, but you can do it via entries in fstab.

Install and run ntfs-config:
```
sudo aptitude install ntfs-config
```

Once installed, to run it, I think it's in the System Tools menu but I'm not at my dual-boot machine. Otherwise start it with "ntfs-config" in terminal.

The app will step you through and make the appropriate fstab entries. 

Come back if you have any questions, or mark it solved if everything works!

Here is a link to ntfs-config. It's a small site but there are some screenshots:
[Ntfs-config]("http://flomertens.free.fr/ntfs-config/")

---

### Post by spookyct on 2008-06-28
it is not mounting my other ext3 partitions either...  I feel like all I have to do is add them to the fstab file, but I am unsure of the proper syntax.

---

### Post by drs305 on 2008-06-28
> **spookyct said:**
> it is not mounting my other ext3 partitions either...  I feel like all I have to do is add them to the fstab file, but I am unsure of the proper syntax.

The standard, basic entry for a non-root (not / ) ext3 partition looks like this. You need to have created the **mountpoint** (/media/mountpoint) and know the **UUID**:
```

UUID=**f69c6913-c385-4cda-af45-244fb7db102e** /media/**mountpoint** ext3 defaults,user 0 2

```

To backup and edit your fstab file (use your text editor - gedit, mousepad, etc):
```
sudo cp /etc/fstab /etc/fstab-bak
gksudo mousepad /etc/fstab
```

To get the UUID number for the partition you are making the entry for:
```
sudo blkid
```

---

### Post by spookyct on 2008-06-29
I added to the fstab file, but the drives did not mount.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=4e62204a-eca5-4442-8f06-6bd40a8940b1 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=f372f85f-e8fc-4c3c-82ae-f8fb02397f90 none            swap    sw              0       0
# /dev/sda4
UUID=62d757c7-e316-4686-940a-c83b4f22a524 /media/disk     ext3    defaults        0       2
# /dev/sdb2
UUID=68D4807DD4804F6E /media/BigDisk ntfs-3g force 0 0

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

---

### Post by drs305 on 2008-06-29
Do the mount points exist?  /media/disk  and  /media/BigDisk

Did you check the uuid's with the **sudo blkid** command to make sure they match? If they are different than those in fstab, change the fstab entries to match.

Added:
You might also try changing the ownership of the mountpoints to yourself if you are the sole user:
```

sudo chown -R username:username /media

```

---

### Post by spookyct on 2008-06-29
Yes the UUID's are correct.  I think..  

```
/dev/sda1: UUID="4e62204a-eca5-4442-8f06-6bd40a8940b1" TYPE="ext3" 
/dev/sda2: TYPE="swap" UUID="f372f85f-e8fc-4c3c-82ae-f8fb02397f90" 
/dev/sda3: UUID="15B641FC04E12298" TYPE="ntfs" 
/dev/sda4: UUID="62d757c7-e316-4686-940a-c83b4f22a524" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb2: UUID="68D4807DD4804F6E" LABEL="BigDisk" TYPE="ntfs" 
/dev/sdb5: UUID="2C38A8C638A88FFE" TYPE="ntfs" 
```


I'm not sure if the mount points exist or not.  To mount the drives, I usually go through the file browsing GUI to "Storage Media", right click, and select mount.

When I do it this way, /media/disk and /media/BigDisk are always the paths.  Also, after editing the fstab file and restarting, I am getting permission errors when I try to mount that way.

---

### Post by drs305 on 2008-06-29
Does xbuntu use nautilus? In gconf-editor there is a setting for nautilus to automount partitions:

```

gconftool-2 --type bool --set /apps/nautilus/preferences/media_automount 'true'

```

You can run the following if you aren't sure if the mountpoints exist. If they do exist you will get an error saying they exist but it won't hurt anything.
```

sudo mkdir /media/disk
sudo mkdir /media/BigDisk
sudo chown -R **username:username** /media

```

Added:
After making any changes you can run the following commands to see the effects. You will get some error messages as it won't allow you to unmount some of the partitions in use, such as root but that is ok.
```

sudo umount -a
sudo mount -a

```

---

### Post by spookyct on 2008-06-29
I ran that command... without an error, so I guess it executed.

I will restart..

---

### Post by spookyct on 2008-06-29
I got an error about mounting to a directory that already exists...

---

### Post by spookyct on 2008-06-29
I also removed the two entries from the fstab file...  I can mount manually to those partitions again.

---

### Post by blitzxp on 2008-07-10
In ubuntu i created the dirs on /media/ (in my case, sudo mkdir /media/Storage ) and then added to fstab:

```
/dev/sda5 /media/Storage ntfs-3g nls=utf8,umask=0222 0 0
```

thats for an **ntfs** partition..

So in your case, for BigDisk:
/dev/sdb2: UUID="68D4807DD4804F6E" LABEL="BigDisk" TYPE="ntfs" 

Make shure you unmount all (sudo umount -a)
You should create the folder /media/BigDisk and then add to fstab:

```
/dev/sdb2 /media/BigDisk ntfs-3g nls=utf8,umask=0222 0 0
```

then sudo mount -a and it should mount correctly ..(and automount)

---

