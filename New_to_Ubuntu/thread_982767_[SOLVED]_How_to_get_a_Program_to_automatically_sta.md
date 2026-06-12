---
title: "[SOLVED] How to get a Program to automatically start during boot up"
date: 2008-11-15
forum: New to Ubuntu
---

### Post by VTT Alps on 2008-11-15
Is there a way to have a program automatically start when I Boot.  For example,  Skype.   I would like that to start when I boot.  

Is there something similar to the Startup Directory in Windows. 

I also have an external Hard drive that "for some reason"  I have to go to Nautilus and click on after booting.   This puts an Icon on my Screen.  Then I can start Rhythm Box.   Otherwise Rhythm Box can't find the files and goes into some kind of mode where it starts looking for files.   Since I have 81 days of music,  It is a very long process.  When this happens,  I have to Re-boot to get Rhythm Box out of this mode.  Just killing it won't work.  Even If I get the disk online and come back it stays in this mode.  Very Frustrating. 

Is there a way to get the Disk Drive to start up at Boot Time without manual intervention.

I'm thinking both of my problems have the same answer. 

Note:  I now use Ubunto 100% of the time for the last 6 months. 

Thanks Ubuntu Community.

---

### Post by cdtech on 2008-11-15
You can add it to the System > Preferences > Sessions to start on boot.

---

### Post by cdtech on 2008-11-15
You could add the drive to the /etc/fstab file to mount on boot......

---

### Post by VTT Alps on 2008-11-16
Thanks for the Reply, However,  I can still not get the disk to mount during boot time.  

In the past I have tried to put the proper mounting information in fstab,  however,  nothing happens.   In fact, after I modify fstab I can not use Nautilus to access the disk, it say's I don't have authorization.  It's strange becasue Root/User/Group all have  Read / Write access.   It's an Internal SATA drive and I have to use a PCI adaptor.  

Here is my fstab file.  The disk in question is the last line (/dev/sda).   I realise there is a # sign in front.  If I remove it and reboot,  I can't start the drive.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=50066034-3663-4cab-9be6-4fe59cb534ea /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=a67527c6-7e8a-44c1-ac46-2fba1c0ab8d2 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
# /dev/sda      /media/disk                             ext2    relatime,errors=remount-ro 0       1

<<<<<<   Here is my mtab file once the disk is running  >>>>>>>

/dev/sdb1 / ext3 rw,relatime,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.24-21-generic/volatile tmpfs rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/cwa/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=cwa 0 0
/dev/sdc1 /media/Elements vfat rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush 0 0
/dev/sda /media/disk ext2 rw,nosuid,nodev,uhelper=hal 0 0


<<<<<   Here is what the mount point looks like.  It is called disk >>>>>>


lrwxrwxrwx  1 root root     6 2008-07-06 11:04 cdrom -> cdrom0
drwxr-xr-x  2 root root  4096 2008-07-06 11:04 cdrom0
drwxr-xr-x  2 root root  4096 2008-07-06 11:04 cdrom1
drwxrwxrwx 12 cwa  root  4096 2008-09-09 21:18 disk
drwx------  7 cwa  root 32768 1970-01-01 01:00 Elements

If you have any advise,  that would be great.  If not,  I can continue using Nautilus to open the Drive.  

Thank you very much.

---

### Post by DoubleMcLovin on 2008-11-16
Just as an experiment, can we try doing the following to your fstab file:

add this line to the bottom instead of what you have
```
/dev/sda /media/disk ext2 rw,nosuid,nodev,uhelper=hal 0 0
```

Are you using ubuntu v: 8.10? I have an external IDE HDD connected through USB and it auto mounts at boot no problem. I wonder if there is a usb daemon that maybe has been disabled on your machine?

---

### Post by CatKiller on 2008-11-16
> **VTT Alps said:**
> Here is my fstab file.  The disk in question is the last line (/dev/sda).

What you're mounting with fstab are *partitions*. You want to mount the partition that has the data on. This might be /dev/sda1, or it might be something else, depending on the partitioning scheme you've used on that disk.

---

### Post by VTT Alps on 2008-11-16
That worked.   Thank you very much.  

Linux support Rocks.

---

