---
title: "Mounting Hard Drives"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by dover19 on 2008-05-27
I'm still new to this and I've never quite understood how to mount Hard Drives when Ubuntu boots.

My fstab must be wrong or something:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=b04d217f-4ce7-493b-9d25-e2b6a174d459 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=a4adc227-5585-4c9d-9670-ae74719747fc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0
/dev/sda1	/media/WinXP	ntfs	0	0
/dev/sda2	/media/160 G	ntfs	0	0
```

I added the last two lines myself.

Here's the results of typing sudo fdisk -l
```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xee88ee88

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9983    80188416    7  HPFS/NTFS
/dev/sda2           19123       38913   158971207+   7  HPFS/NTFS
/dev/sda3            9984       18744    70372732+  83  Linux
/dev/sda4           18745       19122     3036285    5  Extended
/dev/sda5           18745       19122     3036253+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 0 MB, 327680 bytes
255 heads, 63 sectors/track, 0 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

```

---

### Post by TeoBigusGeekus on 2008-05-27
Post us the output of
```
mount
```

---

### Post by dover19 on 2008-05-27
```
/dev/sda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)

```

---

### Post by TeoBigusGeekus on 2008-05-27
Please mount the 2 partitions (double click them from places or from /media),then type again 
```
mount
```
and post us the output

---

### Post by hyper_ch on 2008-05-27
are you sure /dev/sdb is formatted at all? Install gparted, run it and make a screen shot of what gparted says about /dev/sdb.

---

### Post by jw5801 on 2008-05-27
Yes, your fstab is incorrect. The last two lines should look like this:
```
/dev/sda1	/media/WinXP	ntfs	**defaults**  0	0
/dev/sda2	/media/160 G	ntfs	**defaults**  0	0
```

You need to tell it what options you'd like it to mount with, which you haven't done currently.

EDIT: Also, the space in the directory of the second entry may cause issues, possibly want to remove it or put quotation marks around it:
```
/dev/sda2	"/media/160 G"	ntfs	defaults  0	0 
```

---

### Post by sisco311 on 2008-05-27
> /dev/sda1    /media/WinXP    ntfs **defaults,umask=007,gid=46**    0    0[FONT=monospace]
[/FONT]/dev/sda2    /media/160**\040**G    ntfs     **defaults,umask=007,gid=46** 0    0If the mount point contains spaces you must use \040 (ascii code of space).

---

### Post by dover19 on 2008-05-27
I just tried jw5801 and sisco311's recommendations and none of them worked.

I used to be able to go into Places>Computer and mount them by double-clicking on the drives but ever since I made the changes to my fstab I can't even SEE the drives anymore. I'll remove the last two lines and reboot, that should allow me to at least be able to mount them the old way and then I'll post the "mount" output as TeoBigusGeekus suggested.

---

### Post by dover19 on 2008-05-27
> **TeoBigusGeekus said:**
> Please mount the 2 partitions (double click them from places or from /media),then type again 
```
mount
```
and post us the output

Here it is:
```
/dev/sda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sda2 on /media/disk type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sda1 on /media/disk-1 type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)

```

---

### Post by jw5801 on 2008-05-27
> **dover19 said:**
> I just tried jw5801 and sisco311's recommendations and none of them worked.

I used to be able to go into Places>Computer and mount them by double-clicking on the drives but ever since I made the changes to my fstab I can't even SEE the drives anymore. I'll remove the last two lines and reboot, that should allow me to at least be able to mount them the old way and then I'll post the "mount" output as TeoBigusGeekus suggested.

Yes, those fstab entries will prevent Gnome from seeing and mounting the partitions.

Try adding the entries back to /etc/fstab and after a boot running:
```
sudo mount -a
```
That should manually mount everything in fstab, should also give us some idea of why they aren't mounting.

---

### Post by TeoBigusGeekus on 2008-05-27
Add these lines at the end of your fstab file
```
/dev/sda1	/media/disk-1	ntfs	relatime     0	     2
/dev/sda2	/media/disk	ntfs	relatime     0       2
```

EDIT:
Don't forget to reboot and tell us what happened...

---

### Post by dover19 on 2008-05-27
> **hyper_ch said:**
> are you sure /dev/sdb is formatted at all? Install gparted, run it and make a screen shot of what gparted says about /dev/sdb.

What's sdb have to do with it since these are all on sda? Anyway, I've installed gparted and it sure looks like sdb is not formatted.

---

### Post by sisco311 on 2008-05-27
Don't forget to create the mount points.
```
sudo mkdir /media/**WinXp**
sudo mkdir "/media/**160 G"**
```

Replace WinXp and 160 G with the mount points from the fstab.
If the *sudo mount -a *command returns without errors next time you reboot the partition will mount automatically.

---

### Post by dover19 on 2008-05-27
> **TeoBigusGeekus said:**
> Add these lines at the end of your fstab file
```
/dev/sda1	/media/disk-1	ntfs	relatime     0	     2
/dev/sda2	/media/disk	ntfs	relatime     0       2
```

EDIT:
Don't forget to reboot and tell us what happened...

Ok, this seams to have done the job! 

So technically, I should be able to replace "disk-1" with "WinXP" and "disk" with "160G" right? 

I'm just curious, how did you come up with that text? It's great that it works now but what about when I get a new computer, or install Ubuntu on my friend's computer...I'd like to understand a bit more how to figure this out.

For example, the "0 2" part, usually it's always "0 0". What made you figure it had to be "0 2" for this to work? And why "relatime" instead of "defaults,umask=007,gid=46" or simply "defaults". I'm looking at my mount output and I can't figure out how you came to this conclusion.

Anyway, thanks everyone for your help, I don't think I've ever gotten so many replies so fast lol.

---

### Post by hyper_ch on 2008-05-27
> **dover19 said:**
> What's sdb have to do with it since these are all on sda?

You never said what exactely your issue is... and in the output you posted it did show an error with /dev/sdb ;) You only said something about fstab/mounting not right but not that it's about /dev/sda

---

### Post by TeoBigusGeekus on 2008-05-27
**dev/sda1**

The device name - can be figured out by
```
sudo fdisk -l
```


**/media/disk-1**

The device's mount point - can be figured out by
```
mount
```


**ntfs**

What is says.


**relatime**

Type 
```
man fstab
```
and 
```
man mount 
```
to learn more.


**0     2**

Can't remember what the first 0 is, but the second one will force your system to check the partitions for errors every 30th (I think) time they are mounted. The root's partition should have a 1 and all the other partitions a 2 at their end for this to happen. If you change the last 2 to 0, then your partitions will never be checked for errors automatically, you will have to do it manually.

---

### Post by jw5801 on 2008-05-27
> **dover19 said:**
> Ok, this seams to have done the job! 

So technically, I should be able to replace "disk-1" with "WinXP" and "disk" with "160G" right? 

I'm just curious, how did you come up with that text? It's great that it works now but what about when I get a new computer, or install Ubuntu on my friend's computer...I'd like to understand a bit more how to figure this out.

For example, the "0 2" part, usually it's always "0 0". What made you figure it had to be "0 2" for this to work? And why "relatime" instead of "defaults,umask=007,gid=46" or simply "defaults". I'm looking at my mount output and I can't figure out how you came to this conclusion.

Anyway, thanks everyone for your help, I don't think I've ever gotten so many replies so fast lol.

You can replace disk and disk-1 with whatever you'd like so long as the directory you give it exists and is empty. If the directories /media/WinXP and /media/160G didn't exist then that would be the reason it wasn't working before.

defaults, relatime etc are all mount options. Having relatime on an ntfs partition is pointless since ntfs doesn't support the relatime option. If you're curious about the options available to you ```
man mount
```will give you lots of information on them.

The two numbers at the end dictate how fsck (filesystem checking) should deal with the partition. The last number should be 1 for the root filesystem (mounted at /), and 2 for others that you want checked, if you don't want a filesystem checked during the boot process put a 0 here. Given that fsck cannot check ntfs you want it to be 0 for your entries, otherwise there's a good chance when fsck goes to check it, it will abort and drop you to a root shell, which can be disconcerting!

---

### Post by dover19 on 2008-05-27
> **hyper_ch said:**
> You never said what exactely your issue is... and in the output you posted it did show an error with /dev/sdb ;) You only said something about fstab/mounting not right but not that it's about /dev/sda

Lol, true. Thanks.

---

### Post by TeoBigusGeekus on 2008-05-27
> **jw5801 said:**
> You can replace disk and disk-1 with whatever you'd like so long as the directory you give it exists and is empty. If the directories /media/WinXP and /media/160G didn't exist then that would be the reason it wasn't working before.

defaults, relatime etc are all mount options. Having relatime on an ntfs partition is pointless since ntfs doesn't support the relatime option. If you're curious about the options available to you ```
man mount
```will give you lots of information on them.

The two numbers at the end dictate how fsck (filesystem checking) should deal with the partition. The last number should be 1 for the root filesystem (mounted at /), and 2 for others that you want checked, if you don't want a filesystem checked during the boot process put a 0 here. Given that fsck cannot check ntfs you want it to be 0 for your entries, otherwise there's a good chance when fsck goes to check it, it will abort and drop you to a root shell, which can be disconcerting!

My system checks ntfs every 30th time and has never had any problem...

---

### Post by jw5801 on 2008-05-27
> **TeoBigusGeekus said:**
> 
...
Can't remember what the first 0 is, but the second one will force your system to check the partitions for errors every 30th (I think) time they are mounted. The root's partition should have a 1 and all the other partitions a 2 at their end for this to happen. If you change the last 2 to 0, then your partitions will never be checked for errors automatically, you will have to do it manually.

Not every 30th, but however often is set with tune2fs (or reiserfstune), the number is an option set in the partition itself rather than in fsck or fstab.

---

### Post by jw5801 on 2008-05-27
> **TeoBigusGeekus said:**
> My system checks ntfs every 30th time and has never had any problem...

Really? Are you sure it actually checks it and doesn't just pass it over every time? There's no fsck.ntfs in /sbin, so I wouldn't think fsck would be able to check it. I don't currently have an NTFS filesystem anywhere to check with though so I can't verify.

---

### Post by dover19 on 2008-05-27
> **jw5801 said:**
> You can replace disk and disk-1 with whatever you'd like so long as the directory you give it exists and is empty. If the directories /media/WinXP and /media/160G didn't exist then that would be the reason it wasn't working before.

Cool, it works. I just changed the fstab to what you had given me earlier and then created the directories using mkdir and it worked.

Actually when I first rebooted only the 160 G was there. Then I noticed that in the fstab I typed in "WinXP" but I had created a directory called "WinXp" (lower case p). So after changing the fstab file to match my directory it worked.

It's funny you would mention the part about fsck checking the drive every 30th time it's mounted because I just booted and it said something about sda3 being mounted for the 32nd time and it had to be checked.

---

### Post by TeoBigusGeekus on 2008-05-27
> **jw5801 said:**
> Really? Are you sure it actually checks it and doesn't just pass it over every time? There's no fsck.ntfs in /sbin, so I wouldn't think fsck would be able to check it. I don't currently have an NTFS filesystem anywhere to check with though so I can't verify.

Can't verify that at the moment (I'm on a xp machine right now), but it certainly doesn't "abort and drop me to a shell".

---

### Post by jw5801 on 2008-05-27
> **TeoBigusGeekus said:**
> Can't verify that at the moment (I'm on a xp machine right now), but it certainly doesn't "abort and drop me to a shell".

Ok, good to know. I had it happen at one point a while ago (not sure if it was with Ubuntu or something else) and that was the reason, must have coded in a redundancy for that particular exit code of fsck since.

---

