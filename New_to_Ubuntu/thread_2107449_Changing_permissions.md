---
title: "Changing permissions"
date: 2013-01-21
forum: New to Ubuntu
---

### Post by gbrowning on 2013-01-21
I used *gksudo nautilus* to consolidate a boatload of files from various old hard drives.  I want to take ownership of all these files.
     using gksudo and nautilus, then highlighting a folder, then selecting "permissions" and changing the user and group then selecting "apply permissions to enclosed files" does not change the permissions for the folders inside that folder.
    using #* sudo chown -R  myself:myself  /whateverfolder   * alsoseems  to change the top layer only.

Looking around it seems that chown -R should do it.   What am I doing wrong????

---

### Post by bab1 on 2013-01-22
> **gbrowning said:**
> I used *gksudo nautilus* to consolidate a boatload of files from various old hard drives.  I want to take ownership of all these files.
     using gksudo and nautilus, then highlighting a folder, then selecting "permissions" and changing the user and group then selecting "apply permissions to enclosed files" does not change the permissions for the folders inside that folder.
    using #* sudo chown -R  myself:myself  /whateverfolder   * alsoseems  to change the top layer only.

Looking around it seems that chown -R should do it.   What am I doing wrong????

Where does the folder reside?  Could it be on a partition that is formated NTFS?

---

### Post by audiomick on 2013-01-22
> **bab1 said:**
> ... on a partition that is formated NTFS?


Yes, good question. NTFS wont take the Linux permissions. 

The gksudo nautilus and the chown method as you describe them seem correct to me. I don't think you are doing anything wrong as such...:-k

---

### Post by gbrowning on 2013-01-22
The folders are on a drive which is MBR and formatted EXT4.  This was at one point a boot drive.  The original partitioning is still intact.
      Might the permissions have been altered by using Nautilus as superuser?

---

### Post by bab1 on 2013-01-22
> **gbrowning said:**
> The folders are on a drive which is MBR and formatted EXT4.  This was at one point a boot drive.  The original partitioning is still intact.
      Might the permissions have been altered by using Nautilus as superuser?
What is the output of ```
mount
```

Is it possible that this partition is mounted read only (ro)?

Where in the file system (partition) is this folder? Could it be something like /home/you/somefolder or /mnt/somefolder/anotherfolder ?  If you want help you need to be more specific.

---

### Post by gbrowning on 2013-01-22
After re-booting the permissions and icons are correct.  This might have been resolved by unmounting and remounting the drive.   Hold on... conducting an experiment.......have a drive in nearly an identical state but with just a bunch of trash on it....GUID, EXT4, no swap,...changed permissions using gksudo and nautilus trying entire drive did not work....unmounted, remounted...still the same....using sudo chown -R me:me  /media/driveX......This worked as expected without rebooting or re-mounting. 
     Thanks for your help gentlemen, the problem is resolved but the mystery remains.  Nautilus under sudo does not seem to be fully recursive until after a reboot?  I do not know how the permissions are stored but perhaps moving the files multiple times and then changing the permissions  made it necessary to reboot to get the markers straight.

---

### Post by gbrowning on 2013-01-22
Bab:
    I had moved files around to clear drives from a RAID5 array that had become troublesome.  The array had gone read-only and was the source of many of the files.  I don't see how but could the origin drive being ro affect the files after they had been copied to the different drive?
   This has changed since yesterday but here is the requested output of *mount*

[I]/dev/sdb1 on / type ext4 (rw,noatime,nodiratime,discard)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /tmp type tmpfs (rw,noatime,mode=1777)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/george/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=george)
/dev/sdf1 on /media/89c95740-5fd4-4a9c-89b3-610d23def21f type ext4 (rw,nosuid,nodev,uhelper=udisks)
/dev/sda1 on /media/646dbd43-89fb-43dd-9cff-444e780565a5 type ext4 (rw,nosuid,nodev,uhelper=udisks)
[/I]

---

### Post by audiomick on 2013-01-22
> **gbrowning said:**
>  Nautilus under sudo does not seem to be fully recursive until after a reboot?  

Now that you mention it, I think I recall having noticed that nautilus doesn't register certain things until you do a refresh. There is an icon in the bar that looks like a blue arrow going in a circle that does this.

It is a while ago, so I can't remember the circumstances exactly, but this  may have been the missing link.

---

### Post by gbrowning on 2013-01-22
Sorry for the oversight, I wanted to change all the folders and files on this drive
*/dev/sdf1 on /media/89c95740-5fd4-4a9c-89b3-610d23def21f type ext4 (rw,nosuid,nodev,uhelper=udisks)*  So I was using sudo chown -R  george:george /media/89c95740-5fd4-4a9c-89b3-610d23def21f

---

