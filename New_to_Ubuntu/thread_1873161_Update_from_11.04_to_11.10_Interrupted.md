---
title: "Update from 11.04 to 11.10 Interrupted"
date: 2011-10-31
forum: New to Ubuntu
---

### Post by kennae1911 on 2011-10-31
Issue:
I was trying to update to 11.10 and during the process my daughter hit the power button on my laptop (which interrupted the install).  During the process I did have the opportunity to select keep my files etc...However once I reinstalled 11.10 on top of the previous operating system which was 11.04 and 10.?? before that, I cant find any of my music or other files...I have a plethora of music that I must have.  Please help, I am an absolute NOOB, who is trying to learn Ubuntu after being a Windows user....Ubuntu is the only operating system I have....Please advise

---

### Post by wildmanne39 on 2011-10-31
Hi, make sure you stop using the computer immediately so it will stop over writing data on your hard drive, you may be able to recover some of it but it is a big task now.

I am not an expert on the subject but here is a link the can help, you will need to boot from the livecd.
[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
I gave you some other links for a second option.

For the future you should back up your data daily, and before every new install or upgrade.
thank you

---

### Post by sandyd on 2011-10-31
> **kennae1911 said:**
> Issue:
I was trying to update to 11.10 and during the process my daughter hit the power button on my laptop (which interrupted the install).  During the process I did have the opportunity to select keep my files etc...However once I reinstalled 11.10 on top of the previous operating system which was 11.04 and 10.?? before that, I cant find any of my music or other files...I have a plethora of music that I must have.  Please help, I am an absolute NOOB, who is trying to learn Ubuntu after being a Windows user....Ubuntu is the only operating system I have....Please advise
please post the output of

```

sudo fdisk -l
sudo mount -l
```

You can paste this in the terminal (Just type "Terminal" in Unity)

---

### Post by kennae1911 on 2011-10-31
```

sudo fdisk -l
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001924b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       16555   132976478   83  Linux
/dev/sda2           16555       24322    62383105    5  Extended
/dev/sda5           23951       24322     2978816   82  Linux swap / Solaris
/dev/sda6           16555       23822    58365952   83  Linux
/dev/sda7           23822       23951     1034240   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 7958 MB, 7958691840 bytes
245 heads, 62 sectors/track, 1023 cylinders
Units = cylinders of 15190 * 512 = 7777280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00036f61

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         756     5741210+   c  W95 FAT32 (LBA)
Partition 1 has different physical/logical endings:
     phys=(714, 190, 42) logical=(755, 225, 22)
Partition 1 does not end on cylinder boundary.
/dev/sdb2             756        1020     2000000   83  Linux
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(714, 190, 43) logical=(755, 225, 23)
Partition 2 has different physical/logical endings:
     phys=(963, 187, 46) logical=(1019, 61, 30)
Partition 2 does not end on cylinder boundary.
/dev/sdb3            1020        1024       30949   82  Linux swap / Solaris
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(963, 187, 47) logical=(1019, 61, 31)
Partition 3 has different physical/logical endings:
     phys=(967, 150, 15) logical=(1023, 79, 52)
Partition 3 does not end on cylinder boundary.
```

```
sudo mount -l

/dev/sda6 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/kennaejeffries/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=kennaejeffries)
/dev/sdb1 on /media/C557-85FA type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sdb2 on /media/4b917617-e627-4864-b6ed-968f3b095e6e type ext3 (rw,nosuid,nodev,uhelper=udisks)
```

---

### Post by sandyd on 2011-10-31
> **sandyd said:**
> please post the output of

```

sudo fdisk -l
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0001924b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       16555   132976478   83  Linux
/dev/sda2           16555       24322    62383105    5  Extended
/dev/sda5           23951       24322     2978816   82  Linux swap / Solaris
/dev/sda6           16555       23822    58365952   83  Linux
/dev/sda7           23822       23951     1034240   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 7958 MB, 7958691840 bytes
245 heads, 62 sectors/track, 1023 cylinders
Units = cylinders of 15190 * 512 = 7777280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00036f61

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         756     5741210+   c  W95 FAT32 (LBA)
Partition 1 has different physical/logical endings:
     phys=(714, 190, 42) logical=(755, 225, 22)
Partition 1 does not end on cylinder boundary.
/dev/sdb2             756        1020     2000000   83  Linux
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(714, 190, 43) logical=(755, 225, 23)
Partition 2 has different physical/logical endings:
     phys=(963, 187, 46) logical=(1019, 61, 30)
Partition 2 does not end on cylinder boundary.
/dev/sdb3            1020        1024       30949   82  Linux swap / Solaris
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(963, 187, 47) logical=(1019, 61, 31)
Partition 3 has different physical/logical endings:
     phys=(967, 150, 15) logical=(1023, 79, 52)
Partition 3 does not end on cylinder boundary.
```

```
sudo mount -l

/dev/sda6 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/kennaejeffries/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=kennaejeffries)
/dev/sdb1 on /media/C557-85FA type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sdb2 on /media/4b917617-e627-4864-b6ed-968f3b095e6e type ext3 (rw,nosuid,nodev,uhelper=udisks)
```
Hmm.

If I would chance a guess, /dev/sda1 would be it. You never overwrote your old linux installation.

Check the Unity Bar (drives are at the bottom of the bar) for it.

if it doesn't show up, 

```

sudo mkdir /mount/sda1
sudo mount /dev/sda1 /mount/sda1
gksudo nautilus /mount/sda1
```

Your old installation should be there. Go into the "home" folder. All your old stuff is there. Make sure you don't copy anything over though - You would be copying as root.

---

### Post by kennae1911 on 2011-10-31
> **sandyd said:**
> Hmm.

If I would chance a guess, /dev/sda1 would be it. You never overwrote your old linux installation.

Check the Unity Bar (drives are at the bottom of the bar) for it.

if it doesn't show up, 

```

[SIZE=4]**sudo mkdir /mount/sda1**[/SIZE]
mkdir: cannot create directory `/mount/sda1': No such file or directory

[SIZE=4]**sudo mount /dev/sda1 /mount/sda1**[/SIZE]
mount: mount point /mount/sda1 does not exist

[SIZE=4]**gksudo nautilus /mount/sda1**[/SIZE]
Could not find "/mount/sda1".

```Your old installation should be there. Go into the "home" folder. All your old stuff is there. Make sure you don't copy anything over though - You would be copying as root.

I feel that we are getting close....I appreciate all of your help

---

### Post by SeijiSensei on 2011-11-01
Use **/mnt** not /mount.  /mnt is a standard directory on all *nix systems.  You'll see it if you run "ls -l /".

---

### Post by kennae1911 on 2011-11-01
> **SeijiSensei said:**
> Use **/mnt** not /mount.  /mnt is a standard directory on all *nix systems.  You'll see it if you run "ls -l /".

so it should read:

[SIZE=4]**gksudo nautilus /mnt/sda1???**[/SIZE]

---

### Post by kennae1911 on 2011-11-01
since it seems that I didn't delete my old system, is it possible to just reboot into it?  I notice that in GRUB I have a 2.6 and a 3.0/sd1 etc....however when I try to boot into the 3.0 my screen turns black with a blinking cursor in the top left corner...

---

