---
title: "[SOLVED] Hardy Heron Second Hard Disk Question"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by chackoge on 2008-07-04
I installed Hardy Heron 8.04 on my machine. I want to use the second hard disk exclusively for Ruby development, i.e. name it /mnt/rubydev. I can't figure out how to do this despite reading some of the Second Hard Disk in Ubuntu threads. Any help would be much appreciated. gc

$ Sudo fdisk -l gets me 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0007cc04

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9355    75144006   83  Linux
/dev/sda2            9356        9729     3004155    5  Extended
/dev/sda5            9356        9729     3004123+  82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b1e7d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9354    75135973+  83  Linux
/dev/sdb2            9355        9729     3012187+   5  Extended
/dev/sdb5            9355        9729     3012156   82  Linux swap / Solaris

I'm assuming that the default installation puts all of the OS on /dev/sda and that I can use /dev/sdb for the purpose above? 

My /etc/fstab file is below. I've commented out the last line but you can see what I was trying to do.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=99e8d8af-3977-42bf-8a29-710031d189da /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=41bd9b83-5ee4-4bf1-97c5-5bff6672254e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
# /dev/sdb 	/mnt/datadisk 	ext3 defaults 0 0

---

### Post by bab1 on 2008-07-04
Has this been solved?

If not, please send the results of:```
df -h
```

and```
mount
```

---

### Post by dominiquec on 2008-07-04
> # /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sdb1
UUID=99e8d8af-3977-42bf-8a29-710031d189da / ext3 relatime,errors=remount-ro 0 1
# /dev/sdb5
UUID=41bd9b83-5ee4-4bf1-97c5-5bff6672254e none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
# /dev/sdb /mnt/datadisk ext3 defaults 0 0 

From the looks of it, your /dev/sdb1 actually holds the root directory.  Ubuntu doesn't always install it on /dev/sda.  Actually, it doesn't matter where it is, what's more important is the disk UUID.

Do a long listing of /dev/disk/by-uuid and you should see the UUID of your second hard disk.  (This should point to /dev/sda1, as per your fdisk results.)

Replace /dev/sdb in the last line with the UUID and mount the file systems again.

Actually, you may not even need to do any of this.  If you're using a newer version of Ubuntu, your disk should be visible from the menu of disks.  Just mount it.  There are additional automatic mounting options from the GUI.

---

### Post by bab1 on 2008-07-04
> From the looks of it, your /dev/sdb1 actually holds the root directory. Ubuntu doesn't always install it on /dev/sda. Actually, it doesn't matter where it is, what's more important is the disk UUID.


I believe this is in error.  UUID is an alias of the block device (/dev/whatever)

Read the man pages on mount and fstab.  A quick look through the man pages on fdisk too.

---

### Post by chackoge on 2008-07-05
Not solved yet. Thanks gc

$df -h

Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1              72G  3.1G   65G   5% /
varrun                503M  104K  503M   1% /var/run
varlock               503M     0  503M   0% /var/lock
udev                  503M   64K  503M   1% /dev
devshm                503M   12K  503M   1% /dev/shm
lrm                   503M   43M  460M   9% /lib/modules/2.6.24-19-generic/volatile
gvfs-fuse-daemon       72G  3.1G   65G   5% /home/chackoge/.gvfs

$mount

/dev/sdb1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/chackoge/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=chackoge)

---

### Post by chackoge on 2008-07-05
Solved by the following inelegant solution. It was time to clean out this machine anyway. Many thanks for your help. gc

a) Disconnect second hard disk. Reinstall Hardy Heron and updates. Shut down.
b) Reconnect second hard drive. Boot up.
c) Add partition to second hard drive (sdb)
$sudo gparted. 
d) Create dir of choice 
$sudo mkdir /mnt/RubyDev
e) $sudo gedit /etc/fstab 
Add the following line 
/dev/sdb1 /mnt/RubyDev ext3 rw,user,exec 0 0
Save and exit
f) Noted some permissions issues so I ran
$sudo chown -R chackoge /mnt/RubyDev/
g) $sudo gparted now shows /dev/sdb1 mounted at /mnt/RubyDev
h)$ df -h shows
/dev/sdb1              69G  180M   65G   1% /mnt/RubyDev

---

