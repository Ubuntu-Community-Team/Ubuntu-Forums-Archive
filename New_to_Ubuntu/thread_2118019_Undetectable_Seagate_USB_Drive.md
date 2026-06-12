---
title: "Undetectable Seagate USB Drive"
date: 2013-02-20
forum: New to Ubuntu
---

### Post by mtgivery on 2013-02-20
Hi All,

I am just in the starting out process and seem to have made a big mistake with seagate usb expansion drive.  I have been using this drive in windows 7 as back up and thought to test if drive worked in Ubuntu 12.1 before I committed.  I plugged in and was auto detected and seemed to be working fine I deleted a few files and then stupidly not knowing how to safely remove the drive I just pulled it out of the usb port.  Now the drive is undetectable in both linux and windows basically neither system sees the drive at all.  Is my drive dead or does anyone know if it is possible to recover it.  Thank you very much for any help

Best Wishes

Michael

---

### Post by omeomi on 2013-02-20
What is the output of this command? (When you have the USB drive connected)
```
$ lsusb
```

Also, if you go to the Disk Utility (just type 'disk' in the Dash and it'll show up) do you see the drive there?

---

### Post by fdrake on 2013-02-20
also the output of the commands:
```

sudo fdisk -l
mount 

```

---

### Post by Mark Phelps on 2013-02-20
Boot into Win7, connect the drive, and then go into the Disk Management utility.  Scroll down the list and see if the drive is shown there -- it would not have a drive letter, if it is there.  Use the option to add a drive letter.  If that works, you will be OK.

---

### Post by rnrfourie on 2013-02-20
> **mtgivery said:**
> Hi All,

I am just in the starting out process and seem to have made a big mistake with seagate usb expansion drive.  I have been using this drive in windows 7 as back up and thought to test if drive worked in Ubuntu 12.1 before I committed.  I plugged in and was auto detected and seemed to be working fine I deleted a few files and then stupidly not knowing how to safely remove the drive I just pulled it out of the usb port.  Now the drive is undetectable in both linux and windows basically neither system sees the drive at all.  Is my drive dead or does anyone know if it is possible to recover it.  Thank you very much for any help

Best Wishes

Michael

Hi Guys, just to piggy-back onto this thread, I have a similar problem except for a few differences, I use a 1TB WD external USB drive and when I ran the test environment the drive was detectable and I could edit, delete files, etc. After I installed  Ubuntu, it does not see the drive. On Win7, no problems, all the data is there. Tried rebooting Ubuntu as well and when it boots up, I can see the 2 partitions on the drive for about a minute (1 Fat32 and 1 NTFS btw) and then it disappears. Appreciate the advice!!

Regards, Renier

---

### Post by johnparker2012 on 2013-02-20
Hi mtgivery,

     There is nothing to worry about your files in seagate usb drive. In case that your drive is dead you can recover all the important files from that drive. This can be done by using any free data recovery software.

Have a nice day :D...

Regards,
John Parker
[http://www.esalesdata.com/index.php/professionals-list/82-lead/265-physician-list](http://www.esalesdata.com/index.php/professionals-list/82-lead/265-physician-list)

---

### Post by mtgivery on 2013-02-20
Hi John

Output from lsusb is

michael@michael-Inspiron-1545:~$ lsusb
Bus 001 Device 003: ID 05ca:180a Ricoh Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
michael@michael-Inspiron-1545:~$ 

The disk utility does not show the usb drive only system hard drive and CD/DVD

Thanks

---

### Post by mtgivery on 2013-02-20
Output for sudo fdisk -l
michael@michael-Inspiron-1545:~$ sudo fdisk -l
[sudo] password for michael: 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x26950acf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       80324       40131   de  Dell Utility
/dev/sda2           81920    30801919    15360000    7  HPFS/NTFS/exFAT
/dev/sda3   *    30801920   338470906   153834493+   7  HPFS/NTFS/exFAT
/dev/sda4       338470910   625141759   143335425    5  Extended
/dev/sda5       434014208   535482872    50734332+  83  Linux
/dev/sda6       616763392   625141759     4189184   82  Linux swap / Solaris
/dev/sda7       338470912   434014207    47771648   83  Linux
/dev/sda8       535484416   616751103    40633344   83  Linux

Partition table entries are not in disk order

and for mountmichael@michael-Inspiron-1545:~$ mount
/dev/sda8 on / type ext4 (rw,errors=remount-ro)
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
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
gvfsd-fuse on /run/user/michael/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=michael)
/dev/sr0 on /media/michael/WIRE_S5_DISC4 type udf (ro,nosuid,nodev,uid=1000,gid=1000,iocharset=utf8,umask=0077,uhelper=udisks2)

Thanks

---

### Post by fdrake on 2013-02-20
it doesn't look very promising so far. Your drive is not being detected by ubuntu at all. Try Mark Phelps advice, even if a do have some doubts..  

does the drive has a led that blinks when you plug it in?
try different computer or OSs if you can.


___________IF NOTHING WORKS AND YOU ARE READY TO TROW IT AWAY DO THIS:----
Is this an usb thumb drive or a big-pocket-style external usb disk?
if it is the latter on , and you have no way to get the drive to work , try to open the plastic container and get the HDD out of it . These HDD are just normal internal HDD that you use in the computer desktop. The only difference is that they are connected to an USB adapter. You can get the adapter off with some tools, and try to plug the HDD directly internal to a PC . There are usually to kind: SCSI and SATA. I hope you have the right  connector available and some luck.

---

### Post by mtgivery on 2013-02-21
The drive is not present in disk management in Windows 7.  Pulling it apart seems a bit extreme at the moment but am getting close. The led light is now flashing where originally was continually on

Thanks

Michael

---

