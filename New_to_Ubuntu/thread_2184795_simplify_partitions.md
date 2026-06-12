---
title: "simplify partitions"
date: 2013-10-30
forum: New to Ubuntu
---

### Post by Futant on 2013-10-30
Hello. I would like some help clearing up my partitions... I dual boot Ubuntu 12.04 and Windows 7, and a year ago also installed Fuduntu (a discontinued distro) so that I had a triple boot system. After some time Fuduntu 'disappeared' from my boot menu, I tried for some time to get it to 'reappear' but gave up after a while, and just left things as they were. I am left with more logical partitions than I need, including 2 swap partitions - 

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x07f2837e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      208844      104391   de  Dell Utility
Partition 1 does not start on physical sector boundary.
/dev/sda2   *      208896    41168895    20480000    7  HPFS/NTFS/exFAT
/dev/sda3        41168896   780639209   369735157    7  HPFS/NTFS/exFAT
/dev/sda4       780640254   976771071    98065409    5  Extended
Partition 4 does not start on physical sector boundary.
/dev/sda5       968601600   976771071     4084736   82  Linux swap / Solaris
/dev/sda6       780640256   869756927    44558336   83  Linux
/dev/sda7       960430080   968591359     4080640   82  Linux swap / Solaris
/dev/sda8       869758976   870782975      512000   83  Linux
/dev/sda9       870785024   960428031    44821504   8e  Linux LVM

Partition table entries are not in disk order
```

Here is a screenshot from GParted if it is more useful -
[IMG]http://i.imgur.com/s4bePxQ.png[/IMG]

I can see that sda1 is Dell Utility, sda2-3 are Windows, and contained within sda4 are Ubuntu and what was Fuduntu. As Ubuntu was installed before Fuduntu, am I right that sda5 and sda6 are the Ubuntu partitions? I want to delete any partitions that are no longer used, which I think are sda7-9. Am I right that only one swap partition is necessary/desirable? I am not familiar with LVM, although I have read about it, but I would have thought that this LVM partition was created when I installed Fuduntu. Is there any way of telling when a particular partition was created?

What I would like at the end of this is the minimum number of logical partitions. Sorry if this is a bit garbled, please let me know if you need more info/clarification. Cheers.

---

### Post by ajgreeny on 2013-10-30
I assume that sda6 is your logical ubuntu partition, and one of the swap partitions was made at the same time as the installation of ubuntu.  I also think you are correct about the LVM being the fuduntu space; fuduntu was a derivative of Fedora which used LVM in the past (not sure now).

To be sure which are your ubuntu install partitions please boot to ubuntu and show the output of command **mount** which will show the partitions mounted and their mountpoints.  For future info, the output of sudo blkid -c /dev/null will also be very useful.

I suspect you will be able to delete the partitions other than sda6 (and the ntfs ones of course) and then make another swap in a better position than either of them are at the moment.  You can then edit /etc/fstasb and add its UUID to the swap entry so it is available to your OS at boot time.  Do you know what the 500MB partition sda8 is, as it is not really big enough to be useful for very much?

---

### Post by Futant on 2013-10-30
Hey, thanks for the reply. This is the output of **mount** -

```
/dev/sda6 on / type ext4 (rw,errors=remount-ro)
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
gvfs-fuse-daemon on /home/futant/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=futant)

```

Don't know what most of that means but I can see that sda6 is my Ubuntu partition. Here is the output of **sudo blkid -c /dev/null** - 
```

/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="3030-3030" TYPE="vfat" 
/dev/sda2: LABEL="RECOVERY" UUID="92E2E7B1E2E7982D" TYPE="ntfs" 
/dev/sda3: LABEL="OS" UUID="00B8457CB8457168" TYPE="ntfs" 
/dev/sda5: UUID="34deed57-638f-4e19-9b00-12b883cd2cf9" TYPE="swap" 
/dev/sda6: UUID="8cdae8ac-a26e-4173-8b7f-7e819dabb621" TYPE="ext4" 
/dev/sda7: UUID="70e46981-fbf7-42c9-8be5-b35834b338f2" TYPE="swap" 
/dev/sda8: UUID="384047c6-61b8-49ad-a0de-2a6e003f06a6" TYPE="ext4" 
/dev/sda9: UUID="yV5jQ8-pOMz-UWIo-daDn-45px-9dr4-eg7QYY" TYPE="LVM2_member" 
```

I was wondering about the 500mb partition (sda8) too, I can only assume it also has something to do with Fuduntu. 

When you say 'make another swap in a better position than either of them are at the moment', where would be a better position? Let's say I've got rid of sda5,7,8,9, I would probably just think to put it next to sda6? Would you say there is actually a need to delete sda5 (Ubuntu swap partition)? Is it in the wrong place now or would it just be in a silly position if I were to delete sda7-9?

---

### Post by Impavidus on 2013-10-30
I think sda8 is a fuduntu boot partition. It's about the right size for one. Not sure about this, but I thought systems didn't like booting from lvm partitions, so a boot partition is to be expected.

---

### Post by ajgreeny on 2013-10-30
I think you may be right that sda5 swap is right at the end of the disk, so you may as well keep it.  Can we also see the output of **cat /etc/fstab** and **free -m** to check that it is being used at the moment.

As for the LVM query, I'm afraid I know almost nothing about using it as I never have had a system with it installed on my machines, and have no knowledge of booting from an LVM partition.

---

### Post by Futant on 2013-10-30
Here is the output of **cat /etc/fstab** and **free -m** -```
futant@futant-Dell-System-XPS-L502X:/$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=8cdae8ac-a26e-4173-8b7f-7e819dabb621 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=34deed57-638f-4e19-9b00-12b883cd2cf9 none            swap    sw              0       0
# swap was on /dev/sda7 during installation
UUID=70e46981-fbf7-42c9-8be5-b35834b338f2 none            swap    sw              0       0
futant@futant-Dell-System-XPS-L502X:/$ free -m
             total       used       free     shared    buffers     cached
Mem:          3919       2752       1166          0        381       1292
-/+ buffers/cache:       1078       2840
Swap:         7973          0       7973
```

Now I think about it, Fuduntu might have had it's own boot loader... would that be on a separate boot partition?

---

### Post by fantab on 2013-10-31
My suggestion is re-install Ubuntu. BACKUP all you important DATA first.

Delete all the partitions from /dev/sda4 onwards, ie, /dev/sda4-sda9.
Boot into Windows and run 'CHDSK'. If you want more space for Linux then SHRINK the /dev/sda3. If not ignore shrinking.
Create Partitions:
/dev/sda4 Extended (All the unallocated space)
/dev/sda5 Logical ?GB  EXT4 Ubuntu / (20-25GB is plenty )
/dev/sda6 Logical ?GB  Ext4 Free (In case you want to install another distro or Ubuntu flavor, or version)
/dev/sda7 Logical ?GB Ext4
/dev/sda8    SWAP.

---

### Post by Impavidus on 2013-10-31
I think you can delete the second swap entry from your /etc/fstab, delete partitions sda7, sda8, sda9 and expand sda6 into the free space, or create a [separate /home partition](https://help.ubuntu.com/community/Partitioning/Home/Moving) in the free space. Use a live disk. This will destroy any files still present in the Fuduntu partition. If your computer doesn't boot afterwards, use [Boot-Repair](https://help.ubuntu.com/community/Boot-Repair). It's unlikely, but your boot process might still be controlled by Fuduntu.

Another suggestion is to make a separate shared data partition to share files between Windows and Linux, if you have any files to share. It may be safer than using the Windows C partition.

Before modifying partitions it's best to make backups of your important files. You shouldn't lose them, but things may go wrong.

---

### Post by Futant on 2013-10-31
OK, thanks everyone :D

> **fantab said:**
> My suggestion is re-install Ubuntu.

Am I likely to run into problems if I keep my current install and just delete sda7-9, reallocating the space? Seems fairly simple (now!), and I'd rather not reinstall at this point. Got everything backed up so if I do mess it up it's not that big a deal...

---

### Post by fantab on 2013-10-31
> **Futant said:**
> 
Am I likely to run into problems if I keep my current install and just delete sda7-9, reallocating the space? Seems fairly simple (now!), and I'd rather not reinstall at this point. Got everything backed up so if I do mess it up it's not that big a deal...

Not really. I just suggested a re-install because we don't do partitons everyday so if you do it right it will be good for long time it will also keep the partition numbers simple, right now they are all over the place. That is all.

---

### Post by oldfred on 2013-10-31
I believe most of the Fedora systems use LVM with a separate /boot as the default install. You can add lvm2 driver in Ubuntu to get it to work with LVM. The main advantage of LVM is that you can easily change partitions around, but if multi-booting often better to just use ext4 for any Fedora type installs. Also standard partition tools do not work with LVM, so you have to use LVM partition tools to modify LVM partitions. 
So if you have no data you want to save in your LVM install you can just delete those partitions.

---

### Post by Futant on 2013-10-31
Feeling much more confident about partitioning now, thanks all :)

---

