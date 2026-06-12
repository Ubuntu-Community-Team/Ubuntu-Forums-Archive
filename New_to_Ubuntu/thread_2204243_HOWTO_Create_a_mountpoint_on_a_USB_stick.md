---
title: "HOWTO: Create a mountpoint on a USB stick?"
date: 2014-02-07
forum: New to Ubuntu
---

### Post by bc.haynes on 2014-02-07
Working from Ubuntu 12.04 on sda, trying to create a mountpoint on a USB 2.0 stick - sdb1.  I have been to ask Ubuntu, NewDocs, Psychocats, the Internet (Googling), and the forums over the last 2 hours and have not foung a solution.

I messed up the USB stick and had to use gparted to delete partitions, create  a partition table, creata a partition, and format it ext4. I have not been able to find a way to create a mountpoint on sdb1** that works**. I have tried:
```
sudo mkdir /media/usb
```
and it did not make the dir on sdb1 (or on sda).
It yielded this:```
ben@MissionControl:~$ sudo mkdir /media/usb
[sudo] password for ben: 
ben@MissionControl:~$
```
So I am unable to use the mount command like this:
```
sudo mount -t ext4 /dev/sdb1 /media/usb
```
I can't figure out where I'm going wrong ](*,)
EDIT: Uh-oh, I have created 4 dirs in /media
I tried several ways to create a /media/usb mountpoint on sdb1 but nothing worked:
```
ben@MissionControl:~$ sudo mkdir /dev/sdb1/media/usb
[sudo] password for ben: 
mkdir: cannot create directory `/dev/sdb1/media/usb': Not a directory
ben@MissionControl:~$ sudo mkdir /dev/sdb1/media
mkdir: cannot create directory `/dev/sdb1/media': Not a directory
ben@MissionControl:~$ sudo mkdir /dev/sdb1 /media/usb
mkdir: cannot create directory `/dev/sdb1': File exists
mkdir: cannot create directory `/media/usb': File exists
ben@MissionControl:~$
```
EDIT2: Uh-oh, I created 4 files in /dev

---

### Post by mikewhatever on 2014-02-07
"So I am unable to use the mount command like this:" 
Why not? does it give you any errors? If yes, can you post them.
USB sticks are supposed to auto-mount in Ubuntu, does't yours?

PS: You probably want to remove the "HOWTO:" from the title, and change "on" to "for".

---

### Post by bc.haynes on 2014-02-07
Evidently not without a mountpoint.
EDIT: Somewhere in that mess above, I did something right. I checked again and it was mounted on /media/usb. 

Would someone please tell me what I did **right,** so I know next time.

---

### Post by Bashing-om on 2014-02-07
bc.haynes; Hi !

As Mike advises, that usb device "should" automount.

With the usb device connected; what returns from terminal commands:
```

mount
sudo fdisk -lu

```
Then we can look at mount points and manually mounting the usb device.

[INDENT][INDENT]it is all in the process
[/INDENT][/INDENT]

---

### Post by bc.haynes on 2014-02-07
```
ben@MissionControl:~$ mount
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
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ben/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ben)
/dev/sdb1 on /media/a1337ec6-dec2-47fc-8baa-ca7fa1ec53eb type ext4 (rw,nosuid,nodev,uhelper=udisks)
```
```
ben@MissionControl:~$ sudo fdisk -lu
[sudo] password for ben: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000390b6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   344934399   172466176   83  Linux
/dev/sda2       344936446   976771071   315917313    5  Extended
/dev/sda5       968914944   976771071     3928064   82  Linux swap / Solaris
/dev/sda6       344936448   659421183   157242368   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 16.0 GB, 16008609792 bytes
129 heads, 4 sectors/track, 60594 cylinders, total 31266816 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b64eb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048    14338047     7168000   83  Linux
```

---

### Post by Bashing-om on 2014-02-07
bc.haynes;  Hey,

Beats me, maybe you were not pulling on the right string ?
As you expected, the outputs look good and the usb drive is mounted.
Correct:
```

sudo mkdir /media/usb
sudo mount -t ext4 /dev/sdb1 /media/usb

``` Is valid and more correct.
This "mkdir /media/usb" merely makes a directory from which  the file system (sdb1) MAY be attached to the mother file system "/".
Now Attach that file system -> "mount /dev/sdb1 /media/usb"
Once mounted one can access the sdb1 device ! 
For example:
```

ls -la /media/usb
cp ~/MyFile /media/usb/<some_directory_name>/MyFile-backup

```
As the file system here is "ext4" you may omit the "-t ext4" as that is the default.
Thus:
```

sudo mount /dev/sdb1 /media/usb

```
will suffice.
Cleanup: delete all the other extraneous "mount points" in the media directory.

RemeMbeR: If one mounts a device, one MUST un-mount it ! Else file system corruption - at some level - will result !
```

sudo umount /media/usb

```


And just
[INDENT][INDENT][INDENT]keep on keep'n on
[/INDENT][/INDENT][/INDENT]

---

### Post by bc.haynes on 2014-02-07
Thank you,** Bashing-om** for sorting this out for me.

---

### Post by Bashing-om on 2014-02-07
bc.haynes; Hey ! No Problem.

We are all in this together .

If this situation is concluded, please mark this thread solved: 1st post -> thread tools.

As we merrily 
[INDENT][INDENT]move on to other things
[/INDENT][/INDENT]

---

