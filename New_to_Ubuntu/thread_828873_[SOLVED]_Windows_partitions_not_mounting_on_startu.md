---
title: "[SOLVED] Windows partitions not mounting on startup"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by senewag on 2008-06-14
Hi,
I dual-boot with windows "C" and "D" on one partition and Ubuntu on the other.
When I first start up the computer and look at System Monitor it only shows my Ubuntu partition  /dev/sdb2/ and not my windows "C" /dev/sdb1 or "D"  /dev/sda1 .
But if I then run Nautilus, and click on "C" or "D" it opens them up and immediately System Monitor recognises and displays them.  

When I start up Thunderbird (without going first to Nautilus) an error message pops up saying:

"Thunderbird is already running, but is not responding.  To open a new window you must first close the existing Thunderbird process or restart your system".    

Thunderbird's profile is on my "C" drive.
So what I do is.. run Nautilus and click on my "C drive".. problem solved.

Does anyone know what I should do to make System Monitor recognise my Windows partition (my "C" and "D") upon startup?

Thanks for any suggestions.

---

### Post by sharks on 2008-06-14
this will help u:

[http://ubuntuforums.org/archive/index.php/t-1886.html](http://ubuntuforums.org/archive/index.php/t-1886.html)

[www.ubuntuforums.org/archive/index.php/t-35302.html](www.ubuntuforums.org/archive/index.php/t-35302.html)

---

### Post by conscious on 2008-06-14
You need to edit your /etc/fstab file. There are some guides (on these forums as well, see e.g. [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131) , [http://www.google.ru/search?q=mount+windows+partitions+site%3Aubuntuforums.org](http://www.google.ru/search?q=mount+windows+partitions+site%3Aubuntuforums.org) ).

There are also tools that edit /etc/fstab automatically, such as pysdm (it's a graphical tool).

---

### Post by irshadcharm on 2008-06-14
Can anyone help out how to automount windows partitions in startup...Im not able to distinguish between which is linux partition and which is windows partition...i used a wubi installer...and please give a detailed explanation on how to edit the fstab file...

Operating System : Ubuntu Hardy

please help me out...

```
sudo fdisk -l
```

returned the following o/p:

```
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x16391638

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            3825       14593    86501992+   f  W95 Ext'd (LBA)
/dev/sda5            3825        7648    30716248+   b  W95 FAT32
/dev/sda6            7649       11472    30716248+   b  W95 FAT32
/dev/sda7           11473       14593    25069401    7  HPFS/NTFS

```

---

### Post by ukripper on 2008-06-14
can you post output of the following:
```
sudo mount
```
```
cat /etc/fstab
```

---

### Post by senewag on 2008-06-14
Hi,
Thanks to everyone for your help (after just a few minutes of posting this)..  I have followed the links you suggested, learnt a lot and tried editing fstab with different combinations but so far have not successed.
System Monitor shows this:
/dev/sdb2     /               ext3       (ubuntu)
/dev/sdb1     /mediaData___   fuseblk    (my "D" drive (underscore is no type)) 
/dev/sda1     /mediadisk      fuseblk    (my "C" drive)

I got my UUID values from "sudo /sbin/vol_id device".

My /etc/fstab shows the following:
  proc /proc proc defaults 0 0
  UUID=1a66c670-2054-4557-8516-90cf46ce31a5  /  ext3 defaults,           errors=remount-ro 0 1
  /dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
  /dev/fd0 /media/floppy0 auto rw,user,noauto,exec 0 0

Can anyone calculate from this, what extra lines I need to insert into fstab?
Much appreciated for any help...:)

---

### Post by Victormd on 2008-06-14
> **senewag said:**
> Hi,
Thanks to everyone for your help (after just a few minutes of posting this)..  I have followed the links you suggested, learnt a lot and tried editing fstab with different combinations but so far have not successed.
System Monitor shows this:
/dev/sdb2     /               ext3       (ubuntu)
/dev/sdb1     /mediaData___   fuseblk    (my "D" drive (underscore is no type)) 
/dev/sda1     /mediadisk      fuseblk    (my "C" drive)

I got my UUID values from "sudo /sbin/vol_id device".

My /etc/fstab shows the following:
  proc /proc proc defaults 0 0
  UUID=1a66c670-2054-4557-8516-90cf46ce31a5  /  ext3 defaults,           errors=remount-ro 0 1
  /dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
  /dev/fd0 /media/floppy0 auto rw,user,noauto,exec 0 0

Can anyone calculate from this, what extra lines I need to insert into fstab?
Much appreciated for any help...:)

Check the [how to on my signature]("http://ubuntuforums.org/showthread.php?t=802699")...

---

### Post by Joeb454 on 2008-06-14
*Shameless plug of my how-to*

It's the link at the bottom of my sig :) It's worked every time for me :) For both XP and Vista

---

### Post by Troll_the_Great on 2008-06-14
There is an easier way.You just install NTFS Configuring Tool and that takes care of it.See this link:

[http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)

---

### Post by rraj.be on 2008-06-14
YUP.

NTFS config tools will be much helpful GUI and a good alternative to avoid get messing up with fstab:lolflag:

---

### Post by Joeb454 on 2008-06-14
If you checked out the How-To I wrote from the link at the bottom of my sig - you would find that I've recommended using this, and also provided pictures along the way :)

---

### Post by senewag on 2008-06-14
Hi,
Thankyou  everyone of you for the helpful replies.
The end result is that I have got it working!
Using NTFS Configuring Tool.  I tried it earlier on in the evening but it didn't seem to be working for me, do I discarded it.  Then just now, I used it, ticked the box, rebooted.. it did nothing!  Tried it again, this time it detected my partitions.. success.  :)

---

### Post by Joeb454 on 2008-06-14
Congrats :) You can mark your thread solved from "Thread Tools" at the top of this page

---

### Post by irshadcharm on 2008-06-14
> **ukripper said:**
> can you post output of the following:
```
sudo mount
```
```
cat /etc/fstab
```

**_I/p:_**

```
sudo mount
```

**_O/p:_**

```
/host/ubuntu/disks/root.disk on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-18-generic/volatile type tmpfs (rw)
/host/ubuntu/disks/boot on /boot type none (rw,bind)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/irshadcharm/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=irshadcharm)
/dev/sda1 on /media/disk type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sda5 on /media/disk-1 type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
/dev/sda6 on /media/disk-2 type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)


```

**_I/p:_**

```
cat /etc/fstab
```

**_O/p:_**

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

---

### Post by rraj.be on 2008-06-14
irshadcharm   ..

Now are you having the same problem?

---

### Post by irshadcharm on 2008-06-15
hi raj im also from tamilnadu...by the way how do u automount the windows partitions automatically when ubuntu is launched?....its a pain mounting manually...waiting for replies...ive posted by sudo fdisk -l and cat /etc/fstab o/p in the above posts...

---

### Post by irshadcharm on 2008-06-16
can anyone help to automount all my windows partitions ? i have already posted the o/p...please help....

---

### Post by rraj.be on 2008-06-16
see here,.

```
[http://www.psychocats.net/ubuntu/mountwindows]("http://www.psychocats.net/ubuntu/mountwindows")
```

Specificaly for fat do this

Open terminal ad type 

```
sudo mkdir /media/windows
sudo gedit /etc/fstab
```

add this line at the bottom

```
/dev/hda5    /media/windows vfat  iocharset=utf8,umask=000  0    0
/dev/hda6    /media/windows vfat  iocharset=utf8,umask=000  0    0
```


wher

---

