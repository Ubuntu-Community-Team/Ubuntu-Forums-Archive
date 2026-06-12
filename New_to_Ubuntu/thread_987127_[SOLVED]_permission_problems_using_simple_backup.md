---
title: "[SOLVED] permission problems using simple backup"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by glendavee on 2008-11-19
I'm sure this has a very simple solution, but obviously I'm not simple enough. I've been using simple backup to back up files to a USB memory stick. Recently I've been unable to run backups because I get the error message  "selected destination is not writable with current permissions"
When I open the permissions tab on the disk preferences "permissions cannot be determined" I recently upgraded to 8.10, but I think problem existed before upgrade.
Running ls -l in terminal gives 

david@david-desktop:/media$ ls -l
total 56
lrwxrwxrwx  1 root  root     6 2006-12-09 18:11 cdrom -> cdrom0
drwxr-xr-x  2 root  root  4096 2006-12-09 18:11 cdrom0
drwx------  5 david root  4096 1970-01-01 01:00 DISK_IMG
drwxr-xr-x  3 root  root 16384 1970-01-01 01:00 sda1
drwxrwxrwx  1 root  root 12288 2008-11-05 12:27 sda2
drwxr-xr-x 10 root  root  4096 1970-01-01 01:00 sda3
drwxr-xr-x 21 root  root  4096 2008-11-19 09:07 sdb1
drwxr-xr-x  2 root  root  4096 2006-12-11 14:01 sdb5
drwxr-xr-x  2 root  root  4096 2006-12-11 14:01 sdc1
drwxr-xr-x  2 root  root  4096 2006-12-10 16:54 windows_ntfs


drive in question is DISK_IMG

What do I need to do so simple backup will talk to DISK_IMG?

---

### Post by Dedoimedo on 2008-11-19
Hello,
Maybe you need to change ownership?
Something like sudo chown david:david <target> ...
Dedoimedo

---

### Post by glendavee on 2008-11-19
Thanks,Dedoimedo
I've tried chown and also chmod, as in 

david@david-desktop:/media$ sudo chown david /media/DISK_IMG
[sudo] password for david: 
chown: changing ownership of `/media/DISK_IMG': Read-only file system
david@david-desktop:/media$ 

david@david-desktop:/media$ chmod o+wx /media/DISK_IMG
chmod: changing permissions of `/media/DISK_IMG': Read-only file system
david@david-desktop:/media$ ls -l
total 56
lrwxrwxrwx  1 root  root     6 2006-12-09 18:11 cdrom -> cdrom0
drwxr-xr-x  2 root  root  4096 2006-12-09 18:11 cdrom0
drwx------  5 david root  4096 1970-01-01 01:00 DISK_IMG
drwxr-xr-x  3 root  root 16384 1970-01-01 01:00 sda1
drwxrwxrwx  1 root  root 12288 2008-11-05 12:27 sda2
drwxr-xr-x 10 root  root  4096 1970-01-01 01:00 sda3
drwxr-xr-x 21 root  root  4096 2008-11-19 09:07 sdb1
drwxr-xr-x  2 root  root  4096 2006-12-11 14:01 sdb5
drwxr-xr-x  2 root  root  4096 2006-12-11 14:01 sdc1
drwxr-xr-x  2 root  root  4096 2006-12-10 16:54 windows_ntfs

None of this seems to make any difference, and simple backup still won't talk to the media.

---

### Post by __Ryan__ on 2008-11-19
Does the USB drive itself have a write-protection switch that is accidentally enabled?

---

### Post by glendavee on 2008-11-19
No, its a very simple 4GB stick

---

### Post by __Ryan__ on 2008-11-19
Does /etc/mtab show it as being mounted readonly?

---

### Post by glendavee on 2008-11-19
Here are the contents of /etc/mtab :

/dev/sdb1 / ext3 rw,relatime,errors=remount-ro 0 0
tmpfs /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
/proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,nosuid,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=620 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
lrm /lib/modules/2.6.27-7-generic/volatile tmpfs rw,mode=755 0 0
/dev/sda2 /media/sda2 fuseblk ro,nosuid,nodev,allow_other,blksize=4096 0 0
/dev/sdb1 /media/sdb1 ext3 rw,relatime 0 0
/dev/sda1 /media/sda1 vfat rw 0 0
/dev/sda3 /media/sda3 vfat rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
rpc_pipefs /var/lib/nfs/rpc_pipefs rpc_pipefs rw 0 0
nfsd /proc/fs/nfsd nfsd rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/david/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=david 0 0
/dev/sdg1 /media/DISK_IMG vfat rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush 0 0


Properties of /media/DISK_IMG are currently set to :
owner  -  david
folder access  - create and delete files
file access  -  blank
group   -  root
folder access - none
file access  - blank

If I try to make changes to these, they don't save.

Must be something to do with ownership of the folder, maybe something set by Simple Backup??

---

### Post by glendavee on 2008-11-20
After repeated attempts to change folder permissions using chmod, I finally used Windows to delete everything on drive and repair damaged sectors. This resulted in an empty drive which now works with Simple Backup. Less than satisfactory solution, but delivered desired result.

---

