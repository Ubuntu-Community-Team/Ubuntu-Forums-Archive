---
title: "[SOLVED] Can't change folder permissions/ownership on root'd hard-drive"
date: 2008-11-22
forum: New to Ubuntu
---

### Post by Mega_Fauna on 2008-11-22
Hi,

I have an internally mounted hard-drive which is owned by root. I can't run grsync (even sudo grsync) properly as a result.

When I create a folder on the drive and attempt to change it's ownership to me I get "Operation not permitted".

How do I change the owner of the folder, and of the hard-drive?

/at my wit's end

---

### Post by jpkotta on 2008-11-22
Post the output of ```
mount
```
(while the filesystem in question is mounted).

---

### Post by Mega_Fauna on 2008-11-22
Hi, thanks for the quick response. Here it is:

> **jpkotta said:**
> Post the output of ```
mount
```
(while the filesystem in question is mounted).

/dev/sda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-15-generic/volatile type tmpfs (rw)
/dev/sda1 on /boot type ext3 (rw)
/dev/sda4 on /home type ext3 (rw)
/dev/sdb1 on /media/sdb1 type vfat (rw,utf8,umask=007,gid=46)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sdc1 on /media/Ford_Prefect type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,usefree)
/dev/scd0 on /media/cdrom0 type udf (ro,nosuid,nodev,user=johngalt)

---

### Post by jpkotta on 2008-11-22
> **Mega_Fauna said:**
> Hi, thanks for the quick response. Here it is:



/dev/sda3 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-15-generic/volatile type tmpfs (rw)
/dev/sda1 on /boot type ext3 (rw)
/dev/sda4 on /home type ext3 (rw)
/dev/sdb1 on /media/sdb1 type **vfat** (rw,utf8,umask=007,gid=46)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sdc1 on /media/Ford_Prefect type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077,usefree)
/dev/scd0 on /media/cdrom0 type udf (ro,nosuid,nodev,user=johngalt)

That's your problem.  vfat doesn't understand the concept of multiple users.  A vfat fs has one and only one user, which you can specify with mount options.  This is what I use to mount my USB drive (add similar to /etc/fstab).  The "user" option makes the fs owned by whoever ran the mount command.
```
/dev/sdc1	/media/removable	vfat	rw,user,noauto,fmask=177,dmask=077 	0 0

```

---

### Post by Mega_Fauna on 2008-11-23
> **jpkotta said:**
> That's your problem.  vfat doesn't understand the concept of multiple users.  A vfat fs has one and only one user, which you can specify with mount options.  This is what I use to mount my USB drive (add similar to /etc/fstab).  The "user" option makes the fs owned by whoever ran the mount command.
```
/dev/sdc1	/media/removable	vfat	rw,user,noauto,fmask=177,dmask=077 	0 0

```


Hi, I have done as you instructed (I believe). I updated the /sdb1 line in fstab with yours after having slightly modified it. However, when I run "sudo mount -a", the drive doesn't mount, what am I doing wrong?

Updated fstab:
```
# /dev/sdb1
# UUID=47BB-8118  /media/sdb1     vfat    defaults,utf8,umask=007,gid=46 0       1  (This is the old line I commented out)
UUID=47BB-8118  /media/sdb1	vfat	rw,user,noauto,fmask=177,dmask=077 	0 0 (New line that doesn't mount)
```

---

### Post by jpkotta on 2008-11-23
From the mount manpage:
>               **noauto** Can only be mounted explicitly (i.e., the -a option  will  not  cause  the  file  system  to  be
                     mounted).


---

### Post by Mega_Fauna on 2008-11-23
> **jpkotta said:**
> From the mount manpage:

Hi,

I changed the line as instructed and after a reboot, the hard-drive remounted, but the owner and permissions haven't changed, and I can't create a folder on the drive and give it's ownership/permissions to myself.

I'm thinking of reformatting the drive, which file system should I use?

---

### Post by jpkotta on 2008-11-23
The "user" option only works if *you* mount the drive.  That is, you have to run the command
```
mount /media/sdb1
```
You could put this in a script and make a menu item call the script or something, but the point is your user has to run it.  If you let it mount at boot, then root is mounting it.

There is also a uid/gid option for mount, you can try that too.  If that works, it would always mount as the uid that you specify.

If you use ext3, it will understand different users.  Windows will not read ext3 by default, you need to install a driver for it (that is the main advantage of vfat).

Another solution is to change the fmask/dmask options so anyone can write to the filesystem.```
fmask=111,dmask=000
```

---

### Post by Mega_Fauna on 2008-11-27
jpkotta

Hi, I tried a number of the methods you detailed above but none of them worked for me. So I reformatted to ext3 as you suggested and everything works fine now:D 

Thanks,

The only challenge I had was to 'sudo nautilus' --> Right-click - Properties on the drive --> and give myself permission to write upon the root'd drive.

Thanks again.

---

