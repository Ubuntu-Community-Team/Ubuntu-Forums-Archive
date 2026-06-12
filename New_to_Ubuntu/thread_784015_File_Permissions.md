---
title: "File Permissions"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by burnoutbob on 2008-05-06
Hello there all.

I have just moved over to Ubuntu 8.04 and have been loving it thus far. That is until I attempted to delete some files off my second harddive (which was also my second drive when I was using XP and therefore is formatted in NTFS).

Ubuntu basically wont let me delete anything because I "don't own" the files. However, I went playing in the CLI and chown'd the whole directory and it's contents (there was probably a much better way than the way I did it, and probably be a lot quicker than the hour it took me...I'm new, leave me alone :)) but still Ubuntu is standing firm and refusing.

Can anyone help me change these files ownership? I'd like to set the entire drive to be owned by me, rather than just the files I want to delete, but right now I'll settle for a way of deleting those few files. Thanks!

Additionally, anyone have any idea where my 'Deleted Items Folder' has gone? :)

Thanks, in advance, for your help.

Bob.

---

### Post by kpkeerthi on 2008-05-06
How are you mounting the NTFS drive? Can you post the output fo below commands?
```
cat /etc/fstab
```
```
mount
```
```
ls -ld /mountpoint/of/the/NTFSdrive
```

---

### Post by glennric on 2008-05-06
If the partition is ntfs you can mount it with ntfs-3g and give yourself ownership of all the contents by changing your fstab a little bit.  Find the line in fstab for the partition in question and make it look like
```
UUID=uuid_of_drive mount_point     ntfs-3g    defaults,locale=en_US.utf8,uid=1000,gid=1000   0       1
```
Make sure that your uid and gid are 1000 and adjust accordingly.

---

### Post by glennric on 2008-05-06
I just discovered a nice utility for configuring ntfs drives.  Install ntfs-3g and ntfs-config.  Then you can configure your ntfs drives by going to Applications->NTFS Configuration Tool

---

### Post by burnoutbob on 2008-05-06
Here's the outputs;

cat /etc/fstab

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=7fac19e5-e841-4bc9-837a-ae9cd54787c2 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=5ac70fb4-86ab-4b0b-ac06-c8163b4f5b76 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdb1   /media/windows   ntfs   ro,auto,user,fmask=0111,dmask=0000   0   0

```

Mount

```
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw)
/dev/sdb1 on /media/windows type fuseblk (ro,noexec,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/antony/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=antony)

```

 ls -ld /media/windows/

```
drwxrwxrwx 1 root root 32768 2008-05-05 20:21 /media/windows/

```

It's not a problem mounting the drive. As it mounts fine and I can access the files, play media off the drive, etc, but I just can't delete anything.

---

### Post by burnoutbob on 2008-05-06
Actualy, I carried on reading and follwed the suggestions from Glennric. Worked perfectly first time, no hastle at all.

Thanks all! :)

---

### Post by kpkeerthi on 2008-05-06
> **burnoutbob said:**
> 
 ls -ld /media/windows/

```
drwxrwxrwx 1 root root 32768 2008-05-05 20:21 /media/windows/

```

It's not a problem mounting the drive. As it mounts fine and I can access the files, play media off the drive, etc, but I just can't delete anything.
Yeah. Thats because the folder was owned by root and not by you as you thought it was.

---

