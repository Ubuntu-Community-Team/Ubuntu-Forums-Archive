---
title: "how do I setup a LAMP 4localhost to point to files on XP?"
date: 2008-08-23
forum: Programming Talk
---

### Post by ICEcoffee on 2008-08-23
Hi all

I'm going to setup up a LAMP environment on my fresh Hardy install, I'm sure I can find a howto, but what I'd really like to know is, how do I setup apache for localost to point to my XAMPP htdocs folder on my XP partition? I have to dual boot and don't want the hassle of duplicate files out of sync.

---

### Post by Reiger on 2008-08-23
Make sure you have your XP partition mounted under Hardy also (for me my Vista partition is mounted by default)? Then symlink to the directory containing the files?

---

### Post by wdaniels on 2008-08-23
Assuming you use the standard apache2 packages then apache will be running under the user www-data so you will have to mount the relevant XP filesystem so as to allow this user access. The simplest way would probably be to do this using the uid/gid/umask options for the mount in /etc/fstab (this is necessary because you cannot chmod/chown to set permissions/ownership on a non-Linux filesystem).

If you need more help to understand how to do this, just ask.

---

### Post by ICEcoffee on 2008-08-23
Thaks for the replies guys, but I would struggle with the info given here. Can you point me to a 'howto'? or just plain spell it out for me?

Thanks

---

### Post by wdaniels on 2008-08-23
Will talk you through it. First off please post the output from the command:

```
sudo fdisk -l
```

This command will tell us the device names and filesystem type for each of the partitions on your disk.

Also, if you have already installed apache2 (so that www-data already exists) then make a note of the user and group id numbers as given by these commands:

```
id -u www-data
id -g www-data
```

With this information we can give you the line you need to add into the file /etc/fstab that will cause the XP partition to be mounted in Ubuntu in a way that is suitable for apache.

---

### Post by ICEcoffee on 2008-08-23
Hi wdaniels, 
below is the information you require.
Please note that Ubuntu has correctly listed my various disks and partitions upon install.
So I can manually access the XAMPPs htdocs folder (where all my dev sites live in seperate
folders), through the desktop, by clicking on: /media/DSK02/xampp/htdocs. Of course this partition/folder is not mounted automatically
at bootup time.

thanks for your help

EDIT: oh, on windows the XAMPP folder is not on the 'C' drive but another, so Linux may see it as 'sdb', I'm just guessing.


========================================================

Disk /dev/sda: 80.0 GB, 80026361856 bytes
240 heads, 63 sectors/track, 10337 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x4c3674ee

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         637     4815688+   b  W95 FAT32
/dev/sda2   *         638       10336    73324440    7  HPFS/NTFS

Disk /dev/sdb: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd6efd6ef

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         340     2731018+  12  Compaq diagnostics
/dev/sdb2   *       12831       16354    28306530   83  Linux
/dev/sdb3             341       12830   100325925   83  Linux
/dev/sdb4           16355       20023    29471242+   5  Extended
/dev/sdb5           19894       20023     1044193+  82  Linux swap / Solaris
/dev/sdb6           16355       19741    27206014+  83  Linux
/dev/sdb7           19742       19893     1220908+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdc: 164.6 GB, 164696555520 bytes
240 heads, 63 sectors/track, 21274 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x1ef7f91a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       12458    94182448+   7  HPFS/NTFS
/dev/sdc2           12459       21274    66648960    7  HPFS/NTFS
briand@briand-ubuntu:~$ 

=========================================================

id -u www-data
33

=========================================================

id -g www-data

=========================================================

---

### Post by wdaniels on 2008-08-23
OK, it's not clear then which partition you need; I'm seeing 3 disks here in total, and 4 Windows partitions (2 each on sda and sdc) so since you know where the relevant one is mounted already then you can run:

```
mount
```

...which should tell us which device/partition is currently mounted under /media/DSK02.

---

### Post by ICEcoffee on 2008-08-23
I think its sdb6. Below is the output from the mount command:

briand@briand-ubuntu:/media$ cd DSK02
briand@briand-ubuntu:/media/DSK02$ mount
/dev/sdb6 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/briand/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=briand)
/dev/sdc1 on /media/DSK02 type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
briand@briand-ubuntu:/media/DSK02$

---

### Post by wdaniels on 2008-08-23
It's sdc1:

> **ICEcoffee said:**
> 
/dev/sdc1 on /media/DSK02 type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)

I would suggest you create a mount point for sdc1 such as /media/xp-www in which case the fstab line would be something like:

/dev/sdc1 /media/xp-www fuseblk uid=1000,gid=33,umask=007

Test this as follows (close anything accessing the XP partition first else it won't be possible to unmount it):

```
sudo umount /dev/sdc1
sudo mkdir /media/xp-www
echo /dev/sdc1 /media/xp-www fuseblk uid=1000,gid=33,umask=007 | sudo tee -a /etc/fstab
sudo mount -a
```

This will:

[LIST]
[*]Unmount the partition
[*]Create a mount point at /media/xp-www
[*]Add the line to /etc/fstab to mount the partition there with the necessary options
[*]Call mount to actually mount it
[/LIST]

Assuming this all goes as planned, you should find that you have under /media/xp-www the contents of your XP partition having all files owned by your user (assuming your user has id 1000 as is the default) and the group www-data. The umask option 007 should make the permissions of all files 770 (meaning full permissions for your user plus any user in the www-data group, no permission for others).

If this is all correct, then the final thing to do is to create a symbolic link for apache to the relevant folder in the XP partition containing your web files. The command to make the link would be something like:

```
sudo ln -s /media/xp-www/<RestOfPathToWWWRoot> /var/www/xp
```

...in which case you should then find the XP web root under localhost/xp (modify as required, but hopefully you get the gist)!

---

### Post by ICEcoffee on 2008-08-23
hey wdaniels, I'll have to wait until Tuesday now to try this out.

Thanks for your help (and time), much appreciated.

---

