---
title: "Partition Names keeps changing in Hardy Heron"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by sanjbmw2001 on 2008-05-05
Hello There

I have a peculiar problem.

under file system I have /media, which is further divided in to /media/Entertainment 1 and /media/Entertainment 3.
My problem is that /media/Entertainment 3 has become /media/Entertainment 3_ and now it is /media/Entertainment 3__ 

Is there a cure for this so that I can go back to my original settings.

Any help is appreciated.

---

### Post by superprash2003 on 2008-05-05
yes you can unmount and mount it back..go to the terminal and type cat /etc/fstab .. and try to locate your drive. it could be /dev/hdb or something like that.. then type sudo umount /dev/hdb .. and then type sudo mount /dev/hdb /media/Entertainment\ 3

---

### Post by lemming465 on 2008-05-05
I'm not sure where the extraneous underscores are accreting from.  To keep it from happening, you could fix the name permanently by adding a line to /etc/fstab.  See "man fstab" and "man mount" for details.  I don't know what the file system type for the device or partition doing that is; typically windows partitions will be ntfs, Linux partitions ext3, and mp3 players or other USB devices vfat (fat32).  So you might need to add something like one of the following:```
# windows
/dev/sda3  /media/windows1    ntfs    defaults,utf8,umask=007 0  1
# linux
/dev/sda6  /media/linux2      ext3    defaults 0 1
# usb
/dev/sdc1  /media/usb-thing   vfat    defaults     0 1

```
External devices are probably better identified by UUID ("universally unique identifier"), so it's OK if the partition device (first column) looks like UUID=xxxxx. You'll need to make sure that the mount point (second column) exists; use something like *sudo mkdir -p /my/mount/point* to ensure that.  You can get the new entry mounted by doing *sudo mount -a*.

---

### Post by sanjbmw2001 on 2008-05-05
Thanks Guys for a prompt reply.

Let me try and explain pictorially

The line circled in red is the problem area.

As you see the mountpoint is /media/Entertainment-3.

Therefore under the filesystem is should show the following:

Filesystem-----media-----Entertainment-3

Unfortunately it shows the following:

Filesystem-----media-----Entertainment -3 and Entertainment -3_ and Entertainment-3__

Each of these folders have their own lost & found folder etc.


I have not created the last to folders but they are there.


Why are they there?
How to avoid (if any errors I am doing ) in the future?

Once again thanks folks.

---

### Post by lemming465 on 2008-05-05
My, looking at your gparted screenshot that disk has had an exciting history, given how out-of-order the partition slots are compared to the partition physical allocations.  Don't let windows play with it; that will try to sort it for you, which tends to cause fstab trauma.  However, none of that should have any effect on the Linux side, or on your Entertainment-3 mount point.

Could we please get the output from the following commands:```
cat /proc/partitions
mount
cat /etc/fstab
ls -l /media
```

---

### Post by sanjbmw2001 on 2008-05-06
Lemming 

as per my requirement and your advice listed below is the asked for.

( by the way the history of the HDD is murky:))

Thank s once again






sanjbmw2001@sanjbmw2001-laptop:~$ cat /proc/partitions
major minor  #blocks  name

   8     0  156290904 sda
   8     1   14844028 sda1
   8     3   45849510 sda3
   8     4   57175335 sda4
   8     5   16988706 sda5
   8     6    6144831 sda6
   8     7    2482011 sda7
sanjbmw2001@sanjbmw2001-laptop:~$ mount
/dev/sda4 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-17-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
/dev/sda6 on /media/Entertainment-1 type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sda5 on /media/Drive D on XP type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sda3 on /media/Entertainment-3 type ext3 (rw,nosuid,nodev,uhelper=hal)
/dev/sda1 on /media/WINDOZE type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
sanjbmw2001@sanjbmw2001-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=1baac7d7-b6ff-41f9-9ee1-cdf78d9c4bb1 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda7
UUID=5dc039df-fc23-457f-8623-382097c2c457 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
sanjbmw2001@sanjbmw2001-laptop:~$ ls -l /media
total 32
lrwxrwxrwx  1 root        root     6 2008-02-23 05:39 cdrom -> cdrom0
drwxrwxr-x  2 root        root  4096 2008-02-23 05:39 cdrom0
drwxrwxrwx  1 root        root  4096 2008-05-05 22:38 Drive D on XP
drwxrwxrwx  1 root        root  4096 2008-05-06 00:31 Entertainment-1
drwxrwxr-x  8 sanjbmw2001 root  4096 2008-03-23 18:08 Entertainment-3
drwx------ 11 sanjbmw2001 root 16384 1970-01-01 05:30 WINDOZE
sanjbmw2001@sanjbmw2001-laptop:~$

---

### Post by sanjbmw2001 on 2008-05-06
If need be I am willing to reinstall Ubuntu 8.04 from scratch.
But would prefer to have instructions so that the HDD has no exiting history

---

### Post by louieb on 2008-05-06
My partition names don't change in Hardy.  What I did was use VisParted  ( a fork of GParted)  and  put a volume label on my partition. Now they show up under the name on the label. VisParted is available on the [PartedMagicCD]("http://partedmagic.com/wiki/PartedMagic.php?n=Main.PartedMagic")

To use right click on the partition and choose volume label  and give it whatever name you want.

---

### Post by lemming465 on 2008-05-08
In your partitions / mount / fstab / ls posting, your Entertainment-3 partition was mounted where you want it already, and there weren't extra directories in /media unrelated to mounted partitions, so that should have been about right.

If it's still causing problems, try adding this to /etc/fstab```
/dev/sda6  /media/Entertainment-1 ext3 defaults 0 1
/dev/sda3  /media/Entertainment-3 ext3 defaults 0 2
```

---

### Post by sanjbmw2001 on 2008-05-09
Gentlemen

I thank you for your time.

Your advice has been most useful.

I last question:

I exclusively use Ubuntu ( for about a year now ) but still have my windoze.
In your esteemed opinion, it is time to let go of Windoze?

---

### Post by utUtu on 2008-05-09
> **sanjbmw2001 said:**
> Gentlemen

I thank you for your time.

Your advice has been most useful.

I last question:

I exclusively use Ubuntu ( for about a year now ) but still have my windoze.
In your esteemed opinion, it is time to let go of Windoze?

If it's not bothering you, leave it there to rust.  If you need the space, or if you are not going to use it anymore, then by all means wipe it off.

I use it sometimes, or I need to do voice chat, so I have a VirtualBox/xp setup.

---

