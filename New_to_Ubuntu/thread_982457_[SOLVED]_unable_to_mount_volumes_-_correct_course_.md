---
title: "[SOLVED] unable to mount volumes - correct course of action requested"
date: 2008-11-14
forum: New to Ubuntu
---

### Post by simontaylor on 2008-11-14
Dear Ubuntusers,

8.10 failed to open the other drives - volumes? - in my system / computer, giving me the options below.
> 
$LogFile indicates unclean shutdown (0,0) Failed to mount '/dev/sda2': Operation not supported Mount is denied because NTFS is marked to be in use. Choose one action: Choice 1: If you have Windows then disconnect the external devices by clicking on the 'Safely Remove Hardware' icon in the Windows taskbar then shutdown Windows cleanly. 
Choice: 2: If you don't have Windows then you can use the 'force' option for your own responsibility. For example type on the command line: mount -t ntfs-3g /dev/sda2/media/disk -o force   
Or add the option to the relevant row in the /etc/fstab file: /dev/sda2 /media/disk ntfs-3g force 0 0

:confused:

I don't have windows open. ... and adding a force to the fstab seems a bit radical. Or is it?

Help would be greatly appreciated.

(also tried to upload screenshot image (png) to this thread, failed... possibly because wrong URL?)

Best,

Simon Taylor

---

### Post by Rocket2DMn on 2008-11-14
Can you please tell us what error is being presented?  Also please post the output of the following commands:
```
sudo fdisk -l
cat /etc/fstab
sudo blkid
mount
```
If you have any external drives plugged in, please tell us as well (they should not have entries in fstab).

---

### Post by Duck2006 on 2008-11-14
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by simontaylor on 2008-11-14
error = unable to mount volume

> Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0008806d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2611    20972826    7  HPFS/NTFS
/dev/sda2            2612       26485   191767905    7  HPFS/NTFS
/dev/sda3           26486       28562    16683502+  83  Linux
/dev/sda4           28563       30401    14771767+   5  Extended
/dev/sda5           30235       30401     1341396   82  Linux swap / Solaris
/dev/sda6   *       28563       30158    12819807   83  Linux
/dev/sda7           30159       30234      610438+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 25.5 GB, 25590620160 bytes
255 heads, 63 sectors/track, 3111 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbdf68f07

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3111    24989076    c  W95 FAT32 (LBA)

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=b531679a-5000-4c96-aaa7-7fd5e5b7b8aa /               ext3    defaults,errors=remount-ro,relatime 0       1
# /dev/sda7
UUID=5d2cb925-f4e0-4630-b3a2-d818e5ef7fbf none            swap    sw              0       0

/dev/scd0 	/media/cdrom0 	udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

> /dev/hda1: TYPE="ntfs" 
/dev/hda2: TYPE="ntfs" 
/dev/hda3: UUID="bb50905b-4ffd-4a3e-8b41-71acdbef96e6" SEC_TYPE="ext2" TYPE="ext3" 
/dev/hda5: UUID="924015a9-7747-4447-b713-0a5a4b4b2cdb" TYPE="swap" 
/dev/hdb1: LABEL="MAIN" UUID="2239-190B" TYPE="vfat" 
/dev/sda1: UUID="658470186718B095" TYPE="ntfs" 
/dev/sda2: UUID="2E00E373452D8BB6" TYPE="ntfs" 
/dev/sda3: UUID="bb50905b-4ffd-4a3e-8b41-71acdbef96e6" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="924015a9-7747-4447-b713-0a5a4b4b2cdb" 
/dev/sdb1: LABEL="MAIN" UUID="2239-190B" TYPE="vfat" 
/dev/sda6: UUID="b531679a-5000-4c96-aaa7-7fd5e5b7b8aa" TYPE="ext3" 
/dev/sda7: TYPE="swap" UUID="5d2cb925-f4e0-4630-b3a2-d818e5ef7fbf" 

> /dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/simon/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=simon)


---

### Post by simontaylor on 2008-11-14
no external drives --- a master and old win 98 slave

---

### Post by Rocket2DMn on 2008-11-14
That is quite a few partitions there, specifically which ones won't mount when you try to?  More importantly, which ones do you want mounted?

sda3 and sda5 seem to be a separate linux install (another ext3/swap pair) - are you triple booting between Ubuntu, Vista, and something else (like another Ubuntu install, or another flavor of linux)?

I see that your sdb drive is the old Win98 drive you mentioned.

sda6 and sda7 seem to be the partitions used by the linux installation that you are booted into right now (their UUIDs appear in fstab).

---

### Post by SuperSonic4 on 2008-11-14
```
sudo mount -t ntfs-3g /dev/sda2/media/disk -o force
```

---

### Post by simontaylor on 2008-11-14
/dev/sda1
/dev/sda2

are the two the NTFS config tool mentioned finds and the two partitions which currently fail to mount.

Strangely there's no problem mounting the others - even the win98.

?

If I use NTFS-config what mount points ought I to name? windows for both?

or is there another solve?

and yes --- many partitions --- I don't know why!

thanks

---

### Post by Rocket2DMn on 2008-11-14
Ah yes, silly me, your first post says sda2.  Unless you boot into windows and restart cleanly, you will have to force the mount.  I recommend the reboot into windows and back if possible, but forcing should not cause a problem.  You currently don't have an entry in fstab for your sda2 drive (in fact the only hard drive partitions that show in fstab is your root filesysem and swap).  If you want to create a fstab entry for sda2, you would run
```
gksudo gedit /etc/fstab
```
then add the line
```
/dev/sda2 /media/windows ntfs-3g defaults,locale=en_US.utf8 0 0
```
Save and close.  You will have to create the mount point
```
sudo mkdir /media/windows
```
Note that the "windows" in /media/windows can be changed to a name of your preference, so long as there are no spaces or special characters in the name.
Then the drive will automount when you boot into Ubuntu. For now you will have to force the mount since the filesystem had an unclean shutdown.  If you want to use the /media/windows mount point (after creating it of course), your command would be similar to what SuperSonic4 said
```
sudo mount -t ntfs-3g /dev/sda2 /media/windows -o force
```

You can set the mount points to whatever name you like (are they both Windows installations?).  The first NTFS partition is often a recovery partition that you wouldn't want mounted.

---

### Post by simontaylor on 2008-11-14
thanks SuperSonic4 but I want to farm out large image and sound files to the larger drive --- for some reason my 8.10 partition is quite small --- so mounting through sudo mount would be a bit of a pain.

8.04 mounted from the menu no problem --- even without the NTFS-config tool.

---

### Post by bodhi.zazen on 2008-11-14
You should boot to windows and let windows fix the errors, if any, with your ntfs file systems. Then shutdown properly.

If you are not using windows, pull the data off those ntfs partitoins and format them to a linux native file system.

Your other option is to force the mount as outlined by SuperSonic4. Take care though, there is some risk of data loss or damage to your file system.

---

### Post by Duck2006 on 2008-11-14
What ever mount point you want, ie win 1, wein2, just make sure you know what mount point is for what partition.

---

### Post by simontaylor on 2008-11-14
will open windows and see what's up in there.

if not the problem -- will return to your advice.

thanks so far ...

---

### Post by simontaylor on 2008-11-14
A quick reboot into XP and the sda1 and sda2 are mounting without problems from the menu in 8.10. 

How embarrassingly simple! 

Thank you all.

Simon Taylor

---

