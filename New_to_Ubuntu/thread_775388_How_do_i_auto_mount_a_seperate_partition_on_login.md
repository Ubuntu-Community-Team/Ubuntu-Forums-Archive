---
title: "How do i auto mount a seperate partition on login?"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by pjones0404 on 2008-04-30
i recently installed 8.04 and would like to have the separate partitions on my laptop mount automatically when i log in. 

i would like to have a desktop icon for this. i have made the change in gconf-editor to show volumes on the desktop but they do not appear when i log in. if i access them via nautilus then the icons appear. i think that this is due to a mounting issue and that i need to set the volumes to mount automatically. 

i think that i need to make the changes in fstab but i am not sure of what to change exactly. i appreciate any help. 

thanks.

---

### Post by natrixgli on 2008-04-30
A quick search revealed this very thorough guide:

[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

Also in a terminal you can type 'man fstab' for an explanation.


Cheerio,

-n8

---

### Post by Whukes on 2008-04-30
What type of partition are you trying to mount ie. Ext3, NTFS, etc...

---

### Post by pjones0404 on 2008-04-30
thanks for the replies. i am wanting to mount a NTFS and a FAT partition. when i access them through nautilus the icons appear right away. I was also curious if it could be a authorizations issue.

i saw the post regarding fstab but i was not really interested in learning all the ins ans outs of it. i figured that this was a pretty common issue that some one could give me a few tips. 

thanks again.

---

### Post by pjones0404 on 2008-04-30
just wanted to see if the morning crowd had any information on this. 

here is a copy of my fstab in case it is any help. 

[I]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=954d72fe-e52b-4d4c-b248-8040b958cfc5 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=1978c7f7-17e1-4bdd-b11a-0ec410475c97 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0[/I]

thanks again

---

### Post by sisco311 on 2008-04-30
post the output of this commands:

```
mount
```

```
sudo fdisk -l
```

---

### Post by pjones0404 on 2008-04-30
thtanks for the response. here are the outputs. sda 1 and sda 4 are the ones that i would like to mount automatically. 

**Mount**


/dev/sda2 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/jones/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jones)
/dev/sda4 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
/dev/sda1 on /media/disk-1 type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)


**sudo fdisk -l**
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x72fb72fb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3264    26214400+   7  HPFS/NTFS
/dev/sda2            3265        5695    19527007+  83  Linux
/dev/sda3            5696        5819      996030   82  Linux swap / Solaris
/dev/sda4            5820       12161    50942115    b  W95 FAT32

---

### Post by sisco311 on 2008-04-30
i.) create the mount points:

```
sudo mkdir /media/**ntfs**
sudo mkdir /media/**fat**
```You can change the names to whatever you want.

ii.) edit your fstab:
```
sudo gedit /etc/fstab
```and add this lines:
> /dev/sda1    /media/**ntfs**    ntfs    defaults,umask=002,gid=46    0    1
/dev/sda4    /media/**fat   **vfat    utf8,umask=002,gid=46    0   1iii.) mount the partitions:
```
sudo mount -a
```iv.) reboot to check if the partitions are auto-mounted

---

### Post by pjones0404 on 2008-04-30
thanks that worked. the icons are on the desktop as soon as i log in. i will be bookmarking this solution for future reference as well.

one other question. the icons show the size of the drive. is there a way to rename it?

thanks for all the help

---

