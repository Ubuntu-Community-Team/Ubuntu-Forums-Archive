---
title: "Need help with permissions on newly formatted HD"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by tahitiwibble on 2008-11-07
I've just formatted a second internal hard drive with a Live 8.04 CD. I created 2 partitions on the drive and now can't copy to, or use, either of them because they are owned by root.

Please tell me how I can change ownership.

---

### Post by ymra on 2008-11-07
I believe that what you are looking for is chmod.  [http://en.wikipedia.org/wiki/Chmod](http://en.wikipedia.org/wiki/Chmod)

---

### Post by tahitiwibble on 2008-11-08
> **ymra said:**
> I believe that what you are looking for is chmod.  [http://en.wikipedia.org/wiki/Chmod](http://en.wikipedia.org/wiki/Chmod)

Your link led me to "chown" which would appear to be relevant. I just can't follow the technical terms.

How do I change ownership of the two partitions to me.

---

### Post by tahitiwibble on 2008-11-08
Is it not possible to reformat these partitions from within my "system" rather than using the live CD?

---

### Post by m_l17 on 2008-11-08
You can change the owner and group with:

```
$ sudo chown -R username /name-of-partition
```

```
$ sudo chgrp -R username /name-of-partition
```

Replace username with yours.

Take a look at this for more info:

[http://www.tuxfiles.org/linuxhelp/fileowner.html]("http://www.tuxfiles.org/linuxhelp/fileowner.html")

But I would leave root as the owner and group. 

And give everybody read, write and execute:

```
$ sudo chmod -R 777 /name-of-partition
```

```
$ sudo chmod +t /name-of-partition
```

The last "chmod +t" adds the sticky bit, so that people can only delete their own files and sub-directories in a directory, even if they have write permissions to it (see man chmod). Whatever a user creates owns it inside the partition.

Take a look at this for more info:

[http://www.tuxfiles.org/linuxhelp/filepermissions.html#howsymb]("http://www.tuxfiles.org/linuxhelp/filepermissions.html#howsymb")

---

### Post by tahitiwibble on 2008-11-08
The partitions mount on my desktop as "disk" and "disk-1"

This is what happens when I use your code;

dad@dad-desktop:~$ sudo chown -R dad /disk
chown: cannot access `/disk': No such file or directory

---

### Post by m_l17 on 2008-11-08
You need to know where they are mounted. I assumed they where mounted on /

When you created the partitions, did you create a mountpoint?

Like /mnt/disk

---

### Post by tahitiwibble on 2008-11-08
> **m_l17 said:**
> You need to know where they are mounted. I assumed they where mounted on /

When you created the partitions, did you create a mountpoint?

Like /mnt/disk

Please forgive me for flaking out on you last night but I "tried something" and all hell broke loose. I am only now, 20 hours later, back on line.

---

### Post by handydan918 on 2008-11-08
> **tahitiwibble said:**
> Please forgive me for flaking out on you last night but I "tried something" and all hell broke loose. I am only now, 20 hours later, back on line.
 
Perhaps we can get you back on the front page if you post the out put of ```
sudo mount
```
 to start with.\

Perhaps ```
sudo fdisk -l
```. also.

---

### Post by tahitiwibble on 2008-11-08
HandyDan, thanks, but I kind of solved the initial problem by "installing" on the same hard drive and completing the process with my admin name rather than having "anonymously" formatted it.

The problems started when my old faithful backup internal hard drive started freezing the system, stopping boot procedure, etc etc. The drive eventually died completely on me. Fortunately I had a backup of backup, but it's been a tough 20 hours. Now I'm still having trouble with permissions - see [http://ubuntuforums.org/showthread.php?t=975962](http://ubuntuforums.org/showthread.php?t=975962) - any help with this new matter would be greatly appreciated.

---

### Post by tahitiwibble on 2008-11-08
> **handydan918 said:**
> Perhaps we can get you back on the front page if you post the out put of ```
sudo mount
```
 to start with.\

dad@dad-desktop:~$ sudo mount
[sudo] password for dad: 
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
/dev/sda3 on /home type ext3 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/dad/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=dad)


Perhaps ```
sudo fdisk -l
```. also.

dad@dad-desktop:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc535b5b2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2557    20539071   83  Linux
/dev/sda2            9542        9729     1510110    5  Extended
/dev/sda3            2558        9541    56098980   83  Linux
/dev/sda5            9542        9729     1510078+  82  Linux swap / Solaris

Partition table entries are not in disk order




Just in case this may help.

---

