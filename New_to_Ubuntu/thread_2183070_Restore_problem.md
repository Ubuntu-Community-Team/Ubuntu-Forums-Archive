---
title: "Restore problem"
date: 2013-10-23
forum: New to Ubuntu
---

### Post by Brian_Wharton on 2013-10-23
Hi, I am going to swap to 64Bit Ubuntu on my Dell Vostro. So I used the system Backup utility (12.10) to put all the Home files/folders on a 16GB USB drive. I then installed the 64Bit Ubuntu but could not restore the the Thunderbird mail files. HELP!!! Went back to 12.10 but still could not restore the files/folders I backed up.

I am new to Ubuntu, so any answers need to treat me as a newbie.

Thanks,
Brian.

---

### Post by whitesmith on 2013-10-23
Hi and welcome to the forum! The only way to be really secure is to have a separate /home partition. Many people say you don't need one because Ubuntu doesn't overwrite /home in an update anymore, but going from 32 to 64 bits seems to be a case where the separate partition is needed. Also, a second partition allows you to make a clonezilla dup of /home in seconds -- well worth the small inconvenience of creating it in the first place. But this doesn't help you now. Perhaps you could go back to 32-bit and use the backup to save what you need (~/.mozilla) to a flash drive. Then install the 64-bit OS. When that's done, just restore the pertinent directory from the flash drive to your computer.

---

### Post by Brian_Wharton on 2013-10-23
Thanks whitesmith, that's what I'm having problems with. I've gone back to the 32bit system and tried to restore the folders under /home that I backed up on the usb drive under the folder /backup. There is about 10GB of data there but when I try to recover a file or folder, such as /backup/home/ , I get the message Restore Failed, Backup location '/backup/home/' does not exist.

I even tried restoring a single file (the Thunderbird .default file) but it would find that - I know its there, because I extracted one of the archive files and found it. I noticed the .default file is spread over several archive files so I can't just extract them.

---

### Post by whitesmith on 2013-10-23
OK. As before, from the live DVD open a terminal and type```
mount
```Pls post result here. Your device may not be mounted.

---

### Post by Brian_Wharton on 2013-10-24
Results of 'mount' show sdb1 as the USB drive:

brianw@CropDuster:~$ mount
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
gvfs-fuse-daemon on /home/brianw/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=brianw)
/dev/sdb1 on /media/E865-9F40 type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)
brianw@CropDuster:~$

---

### Post by Brian_Wharton on 2013-10-26
Bump. I found the solution after a lot of digging & reading.

I needed to use:

sudo deja-dup --restore

From there the GUI guides you through the archive and asks where to restore the files. The only drawback is you have to reset the permissions for the restored items as they are set to 'root' and not 'user', presumably because the command is carried out as admin.

Cheers,
Brian.:D

---

