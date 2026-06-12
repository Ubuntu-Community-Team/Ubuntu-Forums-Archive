---
title: "Problem with mounting."
date: 2012-08-19
forum: New to Ubuntu
---

### Post by potatoos on 2012-08-19
Lately, I have dealt with a lot of hassle trying to get my external hard drive to work. I am sure that in the process of trying to fix one thing, I ended up messing up something else.
Basically, I can't mount both of my external drives. I can mount either one if the other isn't already mounted. 
Before that, I couldn't see the files on my drive in Windows, but one problem at a time. I need to have them both mounted at once so that I can use one as a back up drive. 

fstab
```

proc /proc proc nodev,noexec,nosuid 0 0
/dev/sdd1 /media/Seagate\040External_ ntfs-3g defaults,nosuid,nodev,locale=en_US.UTF-8 0 0
/dev/sdc1 /media/Seagate\040External ntfs-3g defaults,nosuid,nodev,locale=en_US.UTF-8 0 0
/dev/sdc1 /media/sdc1 ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sdc2 /media/sdc2 ext4 defaults 0 0
/host/ubuntu/disks/root.disk / ext4 loop,errors=remount-ro 0 1
/host/ubuntu/disks/swap.disk none swap loop,sw 0 0
```I don't know if there is anything else that I should provide, but just let me know how to get to the information that I need to post, and I will post it asap.

---

### Post by spjackson on 2012-08-19
You have both sdc1 and sdd1 mounting at the same point: /media/Seagate\040External 
Since you already have another mount point for sdc1, i.e. /media/sdc1, I suggest you remove this line.
```

/dev/sdc1 /media/Seagate\040External ntfs-3g defaults,nosuid,nodev,locale=en_US.UTF-8 0 0

```

---

### Post by potatoos on 2012-08-19
I did as you suggested and deleted that line, but when I plug in the drive, it gives me an error message.
```

Error mounting: mount exited with exit code 1: helper failed with:
mount: only root can mount /dev/sdc1 on /media/sdc1
```

Also, the drive that I am currently using doesn't show up on the fstab. Is that a problem? Can I reset all of my mounts and remount both of my drives?

---

### Post by NikTh on 2012-08-19
Try to change this line 
```
/dev/sdc1 /media/sdc1 ntfs-3g defaults,locale=en_US.UTF-8 0 0
``` 
to this 
```
/dev/sdc1 /media/sdc1 ntfs-3g defaults,**nosuid,nodev**,locale=en_US.UTF-8 0 0
``` 
reboot and test again.
Thanks

---

### Post by potatoos on 2012-08-19
I changed the line like you suggested then rebooted. While booting up, it said that it was trying to mount drives, I pressed S to skip. It said that about three different things. One of the drives was auto mounted upon reboot (the same one that I have been using), but the other one still won't mount. I am getting this error message still:
```
Error mounting: mount exited with exit code 1: helper failed with:
mount: only root can mount /dev/sdc1 on /media/sdc1
```

---

### Post by NikTh on 2012-08-19
Hi  , 
please provide the results of these commands 
```
cat /etc/fstab 
mount 
``` 
Thanks

---

### Post by potatoos on 2012-08-19
cat /etc/fstab 

```

proc /proc proc nodev,noexec,nosuid 0 0
/dev/sdd1 /media/Seagate\040External_ ntfs-3g defaults,nosuid,nodev,locale=en_US.UTF-8 0 0
/dev/sdc1 /media/sdc1 ntfs-3g defaults,nosuid,nodev,locale=en_US.UTF-8 0 0
/dev/sdc2 /media/sdc2 ext4 defaults 0 0
/host/ubuntu/disks/root.disk / ext4 loop,errors=remount-ro 0 1
/host/ubuntu/disks/swap.disk none swap loop,sw 0 0
```

mount

```

/dev/loop0 on / type ext4 (rw,errors=remount-ro)
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
/dev/sda2 on /host type fuseblk (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/sebastian/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=sebastian)
/dev/sdb1 on /media/f324a0f1-8f1d-4924-ac3b-2ccac06d571a type ext4 (rw,nosuid,nodev,uhelper=udisks)

```

---

### Post by bodhi.zazen on 2012-08-19
You have to add the words user and probably auto to the options in fstab

```
/dev/sdc1 /media/sdc1 ntfs-3g auto,users,locale=en_US.UTF-8 0 0
```

I am not sure you really need the options nosuid or nodev

They add a little security, but are not necessary.

---

### Post by potatoos on 2012-08-19
I did what you suggested bodhi.zazen, but it still won't mount the second drive. I get this error now.

```
Error mounting: mount exited with exit code 1: helper failed with:
Unprivileged user can not mount NTFS block devices using the external FUSE
library. Either mount the volume as root, or rebuild NTFS-3G with integrated
FUSE support and make it setuid root. Please see more information at
http://tuxera.com/community/ntfs-3g-faq/#unprivileged
```And this error when trying to mount it from gksudo nautilus (the drive is currently fat32 but was previously ntfs)

```
NTFS signature is missing.
Failed to mount '/dev/sdc1': Invalid argument
The device '/dev/sdc1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
```
Is there no way that I could just start all the mounts over? There seems to be a lot of compatibility issues going on, and it probably has something to do with me reformatting one of the drives to several different formats (ntfs, ext4, fat32) trying to get it recognized.

---

### Post by NikTh on 2012-08-20
Hi , 
you probably have right. Multiple reformats created the problem . Fat32 ? hmmm... ancient filesytem especially for a HDD. Think about to reformat the drive to NTFS , is little better.

Try to add below command to rc.local and see how it will be going. 

```
gksudo gedit /etc/rc.local
``` 
_before **exit 0**_ add this line 
```
mount -a 
``` 
save the document and reboot your system. 
**If something goes wrong** , you can boot from **recovery mode** and click **root** and the give below commands to change the file 
```
mount -o rw,remount /
nano /etc/rc.local
``` 
and delete the line **mount -a **
Thanks

---

### Post by bodhi.zazen on 2012-08-20
> **potatoos said:**
> I did what you suggested bodhi.zazen, but it still won't mount the second drive. I get this error now.

```
Error mounting: mount exited with exit code 1: helper failed with:
Unprivileged user can not mount NTFS block devices using the external FUSE
library. Either mount the volume as root, or rebuild NTFS-3G with integrated
FUSE support and make it setuid root. Please see more information at
http://tuxera.com/community/ntfs-3g-faq/#unprivileged
```And this error when trying to mount it from gksudo nautilus (the drive is currently fat32 but was previously ntfs)

```
NTFS signature is missing.
Failed to mount '/dev/sdc1': Invalid argument
The device '/dev/sdc1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
```
Is there no way that I could just start all the mounts over? There seems to be a lot of compatibility issues going on, and it probably has something to do with me reformatting one of the drives to several different formats (ntfs, ext4, fat32) trying to get it recognized.

Well, if you reformatted your partition from ntfs to fat, you have to update fstab

```
/dev/sdc1 /media/sdc1 ntfs-3g auto,users,locale=en_US.UTF-8 0 0
```

See:

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://wiki.ubuntu.com/MountWindowsSharesPermanently](https://wiki.ubuntu.com/MountWindowsSharesPermanently)
[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

---

### Post by bodhi.zazen on 2012-08-20
> **NikTh said:**
> Hi , 
you probably have right. Multiple reformats created the problem . Fat32 ? hmmm... ancient filesytem especially for a HDD. Think about to reformat the drive to NTFS , is little better.

Try to add below command to rc.local and see how it will be going. 

```
gksudo gedit /etc/rc.local
``` 
_before **exit 0**_ add this line 
```
mount -a 
``` 
save the document and reboot your system. 
**If something goes wrong** , you can boot from **recovery mode** and click **root** and the give below commands to change the file 
```
mount -o rw,remount /
nano /etc/rc.local
``` 
and delete the line **mount -a **
Thanks

That is not necessary if you use a proper entry in fstab and will fail with the same error unless you fix fstab.

---

### Post by NikTh on 2012-08-20
> **bodhi.zazen said:**
> That is not necessary if you use a proper entry in fstab and will fail with the same error unless you fix fstab.

Hi , 
**thanks for the info. **
I thought this command (in rc.local) would mount all the devices automatically in boot, cuz rc.local executed as root.

---

### Post by bodhi.zazen on 2012-08-20
> **NikTh said:**
> Hi , 
**thanks for the info. **
I thought this command (in rc.local) would mount all the devices automatically in boot, cuz rc.local executed as root.

It would do that, but they are mounted automatically already.

The problem is, fstab is saying "ntfs-3g" when it should say "auto" or "vfat".

fix fstab, fix the problem (although your solution shows you are thinking, and that is a good thing).

---

### Post by NikTh on 2012-08-20
Hi , bodhi.zazen
> **bodhi.zazen said:**
> It would do that, but they are mounted automatically already.

The problem is, fstab is saying "ntfs-3g" when it should say "auto" or "vfat".

I used  this message 

> **potatoos said:**
> 
```
Error mounting: mount exited with exit code 1: helper failed with:
mount: only root can mount /dev/sdc1 on /media/sdc1
```
but it seems I missed this 
> **potatoos said:**
> 
```
NTFS signature is missing.
Failed to mount '/dev/sdc1': Invalid argument
The device '/dev/sdc1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
```


> **bodhi.zazen said:**
> (although your solution shows you are thinking, and that is a good thing).
Thanks Guru ! :)

---

### Post by potatoos on 2012-08-21
I changed "ntfs-3g" to "auto" and then to "vfat" and I still can't mount the drive.

I get this error:
```
Error mounting: mount exited with exit code 1: helper failed with:
mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

---

### Post by bodhi.zazen on 2012-08-21
> **potatoos said:**
> I changed "ntfs-3g" to "auto" and then to "vfat" and I still can't mount the drive.

I get this error:
```
Error mounting: mount exited with exit code 1: helper failed with:
mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

Is there something wrong with the hard drive ? It sounds as if you have formatted the partition a few times.

If the hard drive is "OK", format it again and use the auto option

```
/dev/sdc1 /media/sdc1 auto defaults 0 0
```

You can add options as needed, depending on the file system, from the links I gave you on fstab.

---

### Post by potatoos on 2012-08-21
Thanks, everyone! 
I changed the line in fstab like you suggested, bodhi.zazen, then reformatted the drive, and it mounted properly. 
[]("http://ubuntuforums.org/member.php?u=89054")

---

