---
title: "change the permission to access the files in a folder"
date: 2014-05-01
forum: New to Ubuntu
---

### Post by wstay3 on 2014-05-01
I need to change the permission to access the files in a folder named SAMSUNG HP CH. The property page of this folder is as shown in Screenshot-1. I use: sudo chmod u+r+x -R SAMSUNG\ HP\ CH/ as in Screenshot-2, to change the permission to access the files in the folder. After changing permission with no error message from the terminal, I wonder why the permission to access the files in the folder is still unchanged as the property page I get from the folder is still the same as in Screenshot-1

---

### Post by jdeca57 on 2014-05-01
That seems an external drive and the question is of course what filesystem, like [http://ubuntuforums.org/showthread.php?t=1658076](http://ubuntuforums.org/showthread.php?t=1658076)

---

### Post by whitesmith on 2014-05-01
Pls open a terminal and run ```
lshw > test
grep '150GB-BACKUP-1' test
``` and publish the results to give a better picture of your backup drive.

---

### Post by drink1297 on 2014-05-02
Try changing the owner of the drive to root

---

### Post by wstay3 on 2014-05-09
Posting the code:
lshw > test
grep '150GB-BACKUP-1' test
I get: 
> wstay1@DualCoreSS500GbSda6:~$ sudo lshw > test
wstay1@DualCoreSS500GbSda6:~$ sudo grep '150GB-BACKUP-1' test
                      logical name: /media/150GB-BACKUP-1-Spare
wstay1@DualCoreSS500GbSda6:~$ 

The folder and files are not on an external drive.

Changing the owner to root also does not changing anything on the property page of the folder.

> wstay1@DualCoreSS500GbSda6:~$ cd /media/150GB-BACKUP-1-Spare/Source-Backup/TWS
wstay1@DualCoreSS500GbSda6:/media/150GB-BACKUP-1-Spare/Source-Backup/TWS$ sudo chown root SAMSUNG\ HP\ CH/
wstay1@DualCoreSS500GbSda6:/media/150GB-BACKUP-1-Spare/Source-Backup/TWS$
 
The folder and files are on another partition with a NTFS filesystem.
So that means there is no way to change the permission from a linux OS.

---

### Post by coffeecat on 2014-05-09
Since the folder/files in question are on a ntfs partition on an internal hard drive, we need some relevant information, especially about how the partition was mounted:

[list=1][*]What version of Ubuntu are you using?
[*]How are you mounting the ntfs partition - from the file manager or by means of /etc/fstab?
[*]If by means of /etc/fstab, post the output of this terminal command:

```
cat /etc/fstab
```
[*]With the ntfs partition mounted, post the output of this command:

```
mount
```[/list]

---

### Post by wstay3 on 2014-05-13
1. I am using Ubuntu 10.04.
2. After logging on-to Ubuntu desktop and using the file manager Nautilus 2.30.1, I can view and use except changing the permission attributes for the files in the folder on the ntfs partition '150GB-BACKUP-1-Spare' which is on a partition on another harddisk in the same computer.
3. I do not do any mounting of this ntfs partition  by means of /etc/fstab, or by any other means.

Posting: cat /etc/fstab

```
wstay1@DualCoreSS500GbSda6:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=f4cc8f0c-f6e2-4643-a547-4010530906e3 /               ext3    errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=87aa8e19-ab9b-4883-a8ae-83b1bbd03efd none            swap    sw              0       0
# swap was on /dev/sdb8 during installation
UUID=c3daeed8-a79c-4603-a732-28f5ea90ff12 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
wstay1@DualCoreSS500GbSda6:~$ 
```

Posting: mount

```
wstay1@DualCoreSS500GbSda6:~$ mount
/dev/sdb6 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
tmpfs on /run type tmpfs (rw,nosuid,relatime,size=617316k,mode=755)
gvfs-fuse-daemon on /home/wstay1/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=wstay1)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sda5 on /media/150GB-BACKUP-1-Spare type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdb9 on /media/500GB-VIRTUALBOX-W8 type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
wstay1@DualCoreSS500GbSda6:~$
```

From the above postings, the ntfs partition '150GB-BACKUP-1-Spare', is not mount in /etc/fstab.
It is mounted as '/dev/sda5 on /media/150GB-BACKUP-1-Spare' (in /etc/mtab).
```

/etc/mtab:
/dev/sdb6 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
udev /dev devtmpfs rw,mode=0755 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
none /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
tmpfs /run tmpfs rw,nosuid,relatime,size=617316k,mode=755 0 0
gvfs-fuse-daemon /home/wstay1/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=wstay1 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
/dev/sda5 /media/150GB-BACKUP-1-Spare fuseblk rw,nosuid,nodev,allow_other,blksize=4096,default_permissions 0 0
/dev/sdb9 /media/500GB-VIRTUALBOX-W8 fuseblk rw,nosuid,nodev,allow_other,blksize=4096,default_permissions 0 0
```

So, is there a way of changing the permission for the folder and the files in it even-though it is on the ntfs partition?

---

### Post by coffeecat on 2014-05-13
I've replaced quote tags with code tags in your post. You need code tags for terminal output and contents of system files in order to preserve formatting. 

> **wstay3 said:**
> 1. I am using Ubuntu 10.04.

10.04 is long past end-of-life on the desktop. You need to think about upgrading or re-installing to a supported version of Ubuntu.

> **wstay3 said:**
> 
3. I do not do any mounting of this ntfs partition  by means of /etc/fstab, or by any other means.

If the partition was not mounted you would not be able to access it! You are clearly mounting it by clicking on the appropriate line in the left pane of nautilus which causes the system to auto-mount it by means of udev. 

> **wstay3 said:**
> So, is there a way of changing the permission for the folder and the files in it even-though it is on the ntfs partition?

No. You cannot use chmod and chown on ntfs filesystems because they do not support the Linux system of permissions. Permissions of a NTFS filesystem are established by means of mount options. If you wanted something other than the default set of permissions you would need to set up a custom line in /etc/fstab, but that would normally apply to all the files in the mounted filesystem, not a subset. There is a way of more fine-grained control of permissions in a ntfs filesystem with user mapping, but I have never done this. It seems to be a really tedious thing to set up and, furthermore, I don't know whether it would achieve what you want to achieve, which appears to be making files within a particular folder executable. Is this what you are trying to do? Perhaps if you explain what it is you want to do so, someone could help you find another way. Most people wishing to execute files simply choose the simpler option of moving them to a Linux filesystem.

---

