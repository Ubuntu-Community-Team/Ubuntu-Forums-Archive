---
title: "Expanding Home directory"
date: 2013-10-27
forum: New to Ubuntu
---

### Post by LinuxUser666 on 2013-10-27
Hello fellow Ubuntu users, I am running 32-bit Ubuntu 12.10 and I have one simple question to ask.
How do I expand and/or add extra space for my Home directory, I already made one 75 GB ext4 partition but I just did not want to try anything on my own, I do not wanna screw my Linux up.

My regards, stay brutal. :guitar:

---

### Post by ajgreeny on 2013-10-27
Can you show us what partitions you have at the moment by running command ```
sudo fdisk -l
``` or better, from a live ubuntu system from DVD or USB, opening gparted and taking a screenshot of the gparted window which you can add as an attachment to your reply.

---

### Post by LinuxUser666 on 2013-10-27
this is fdisk's printout:
```
 Device Boot      Start         End      Blocks   Id  System/dev/sda1              63   109876373    54938155+   7  HPFS/NTFS/exFAT
/dev/sda2       167890942   624655394   228382226+   f  W95 Ext'd (LBA)
/dev/sda3   *   109877248   167888895    29005824   83  Linux
/dev/sda5       169983828   333830699    81923436    7  HPFS/NTFS/exFAT
/dev/sda6       333830763   497677634    81923436    7  HPFS/NTFS/exFAT
/dev/sda7       497677698   624655394    63488848+  83  Linux
/dev/sda8       167890944   169981951     1045504   82  Linux swap / Solaris


Partition table entries are not in disk order


Disk /dev/sdb: 82.0 GB, 81963220480 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160084415 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000cf516



```

---

### Post by ajgreeny on 2013-10-27
This is a bit convoluted as your partitions are not in numerical order but on the disk they are in the following order
```

/dev/sda1              63   109876373    54938155+   7  HPFS/NTFS/exFAT
/dev/sda3   *   109877248   167888895    29005824   83  Linux
/dev/sda2       167890942   624655394   228382226+   f  W95 Ext'd (LBA)  [COLOR=#ff0000]An extended partition containing:-[/COLOR]

/dev/sda8       167890944   169981951     1045504   82  Linux swap / Solaris
/dev/sda5       169983828   333830699    81923436    7  HPFS/NTFS/exFAT
/dev/sda6       333830763   497677634    81923436    7  HPFS/NTFS/exFAT
/dev/sda7       497677698   624655394    63488848+  83  Linux
```
There appears to be a lot of space at the start of the disk that is not even listed here so I am also confused.  I think a screenshot from gparted would be a great deal more useful, so please try to do that for us.  Can you also please run command mount and report back here the output as it will ensure that the partitions are what I believe them to be, ie, / (root) at sda3 and /home at sda7, with two ntfs partitions on disk between them.

In order to enlarge your /home partition you will have to shrink or delete /dev/sda6, the second of your ntfs (data?) partitions which is next to your /home, but let's see the screenshot first just to be sure.

---

### Post by LinuxUser666 on 2013-10-29
Here is the screenshot from GParted 
[ATTACH=CONFIG]247358[/ATTACH]

here is the output of ```
mount
```:

```
slayer1@Slayer1-desktop:~$ mount/dev/sda3 on / type ext4 (rw)
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
/dev/sda1 on /media/XP type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda5 on /media/radni type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda6 on /media/storage1 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
/dev/sda7 on /media/Storage_Linux type ext3 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfsd-fuse on /run/user/slayer1/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=slayer1)



```

But I simply do not understand why should I touch any of my NTFS partitions when I have one ext3 partition completely free, can't I just merge them somehow? I think I should have specified on which partition I think of, I think of ```
/dev/sda7
``` partition labeled Storage_Linux. 

My regards, stay brutal.

---

### Post by ajgreeny on 2013-10-29
OK, now I understand what you're talking about, but to answer your specific question, unfortunately you can not simply merge the partitions sda3 and sda7 as they are not next to each other.  To do so you would have to move your swap, sda8, and also the two ntfs partitions, sda5 and sda6.

There are three ways to deal with this.

 **1]  Move your data.**
You can simply move all the data folders (Documents, Downloads, Music, Videos, etc etc) in your home to the storage partition sda7 and then link to them from your home folder.

**2]  Make a new /home partition.**
Your ubuntu root partition sda3 is 27.66GB and you do not have a separate /home partition, so everything in your home is just in a folder within that root partition.  If you wish, you could copy everything including all the hidden files and folders currently in home to the empty sda7 storage partition, preferably using a live DVD/USB to avoid files possibly changing while you're copying.  Check that everything has copied then delete all the files in the current /home.  Finally you can edit /etc/fstab to make sda7 become your new home with two lines in the form of```
# /home was on /dev/sda4 during installation
UUID=2a1a9b57-4d0a-4570-974f-d6114fb25ef1 /home           ext4    defaults        0       2
``` though your UUID will not be the same as mine but can be found from command ```
sudo blkid -c /dev/null
```from the live system.
Now when you next boot you should get your new /home partition mounted as needed.  It should be a seamless change as far as you are aware; you will just have a much larger /home available.

  
**3]  Start again with a better partition layout.**
I begin to think it may be easier and quicker to start again, backing up all your files on the ntfs storage partitions, deleting those partitions, then re-installing ubuntu. I would suggest you use all logical partitions for all these as linux will boot from a logical partition easily, unlike windows.  Make a 10-15GB root partition, a new /home partition of a size you think will be big enough, eg 80-90GB and finally a swap partition of 2GB.  The remaining space can be new logical ntfs storage partition or partitions, which will be seen and can be used by both ubuntu and windows.

I hope that helps and does not scare you off totally.  If you need more info or help come back again for more details.

---

### Post by LinuxUser666 on 2013-10-30
Yeah I guess that making new partition table is better than copying everything here and there.
I just wanna ask you is there a way to extract installation packages of my currently installed apps? For example to make me a .deb package of my Google Chrome browser so I do not need to download new packages.

My regards, stay brutal. ):P

---

### Post by ajgreeny on 2013-10-30
You should be able to find debs of many of your personally installed packages in /var/cache/apt/archives, assuming you have installed through the normal channels.  Copy them to a memory flash drive and then later you can simply copy them back to /var/cache/apt/archives on your new install though you will need admin rights to do this.  

Some of the packages may have already been deleted automatically by the system but this it is still worth doing to save time and bandwidth, and is something that I used to do a lot if I had to re-install my system, not something that I have had to do for a long time now.

---

### Post by LinuxUser666 on 2013-10-30
Since we are at the subject, could you please tell me how to change ownership of a some partition from **root** to normal user? Because my sda7 partition is currently owned by root and not by me, so normally I can't write or read from it unless I open it with root privileges. Since you suggest I do copying from live media, do I have to worry about that ownership issue as well? And thanks ajgreeny, you are of much help to me. 

My regards, stay brutal. :guitar:

---

### Post by ajgreeny on 2013-10-30
It looks as if sda7 is your data storage ext3 partition, in which case you need to mount the partition and find its mountpoint in your filesystem (use command **mount** to see where it is mounted) then run command ```
sudo chown slayer1:slayer1 */media/mountpoint*
``` change your username slayer1 if I got that wrong and change the mountpoint entry shown in italics to whatever it is.

Once you have done that you could use rsync to backup all your current /home to sda7 rather than using a live system.

---

### Post by LinuxUser666 on 2013-11-01
This is plenty of information here that should help me to make my partitions in check and have enough space in /home.
Thank you community and special thanks to [COLOR=#000000]ajgreeny.[/COLOR]

My regards, stay brutal. :guitar:

---

