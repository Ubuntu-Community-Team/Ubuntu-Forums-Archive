---
title: "Can't get access links of folders in a ntfs backup partition by default."
date: 2021-08-08
forum: New to Ubuntu
---

### Post by antonio-cpr on 2021-08-08
Hi! 
I'm using Ubuntu last version and I have this ntfs backup partition and I want  to create links for some folders in it at /home/rob/ directory. I tried the following command but everytime I start the system the ownership of these links belongs to root and I can't get access them. Theses links are blocked in Nautilus. To "fix" I need to open Nautilus and click on "Other Locations->413 GB Volume", but I don't want to do that everytime I start the system. 

```
sudo ln -s /media/rob/7C026AC2026A80CE/downloads/ ~/
sudo ln -s /media/rob/7C026AC2026A80CE/musics/ ~/
sudo ln -s /media/rob/7C026AC2026A80CE/pictures/ ~/
```
The path "/media/rob/7C026AC2026A80CE/pictures/" I got at the properties option.

I would like to access these folders normally, like them really would be in /home/rob/ by default. I don't know if I need to auto mount them or change the ownership of them or what?

I don't know if is necessary but here the fstab.
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda6 during installation
UUID=b414d1f2-57f9-4d6e-bed6-dac319424057 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=3e81b38d-1cb2-45e6-b789-cc28d28b3674 none            swap    sw              0       0
```

---

### Post by ActionParsnip on 2021-08-08
Did you check case? Linux is very case sensitive so capital letters matter a lot.

---

### Post by TheFu on 2021-08-09
Don't use sudo.
Ensure the storage is mounted where you have it specified. 

```
cd ~
ln -s /media/rob/7C026AC2026A80CE/downloads
ln -s /media/rob/7C026AC2026A80CE/musics
ln -s /media/rob/7C026AC2026A80CE/pictures
```

Why mount it with 7C026AC2026A80CE in the name?  That's just ugly an unnecessary.

If the storage isn't already mounted, then symbolic links don't work. Also, they won't cause the storage to be mounted.  If you want the storage mounted on-demand, when requested by any method, use autofs.  This is good for USB or network connected storage.  For internal storage, use the /etc/fstab method.
[Https://ubuntuforums.org/showthread.php?t=2464944&p=14048909#post14048909](Https://ubuntuforums.org/showthread.php?t=2464944&p=14048909#post14048909) is for ext4, but it uses labels, which are easier for humans. Step 8 will need to be altered slightly (that's the line which gets placed into the fstab), but everything else except the chmod/chown is relevant.  Those commands don't work on NTFS file systems.  In step 8, change "ext4" to "ntfs" and post the output from the 'id' command so we can add some other options to the mount. We typically need to add ```
uid=thefu,fmask=0002,dmask=0002,nodev,permissions,windows_names,nosuid,noatime,async,big_writes
```
 to the mount options and for NTFS, also needs

---

### Post by antonio-cpr on 2021-08-10
Thanks for your help guys. Problem solved.
I created a /media/backup folder. Then I had to edit /etc/fstab and added the following line:
```
# /dev/sda5
UUID=7C026AC2026A80CE /media/backup ntfs rw,nosuid,nodev,user_id=1000,group_id=1000,allow_other,blksize=4096 0 0
```

And the links are:
```
ln -s /media/backup/downloads ~/
ln -s /media/backup/musics ~/
ln -s /media/backup/pictures ~/
```

I had this configuration from my old system arch linux which I saved the fstab file. I had to find out which is my userid and group id number. I don't know If the line above was correctly edited but everything is working fine, so...

---

### Post by TheFu on 2021-08-10
**big_writes** is an option needed for NTFS mounts to increase performance 20-30%. async and noatime can help a little too.

```
       big_writes
              This option prevents  fuse  from  splitting  write  buffers  into  4K
              chunks,  enabling big write buffers to be transferred from the appli&#8208;
              cation in a single step (up to  some  system  limit,  generally  128K
              bytes).
```


Might want:
```
       atime, noatime, relatime
              The atime option updates inode access time for each access.

              The **noatime** option disables inode access time updates which can speed
              up  file operations and prevent sleeping (notebook) disks spinning up
              too often thus saving energy and disk lifetime.

       windows_names
              This option prevents files, directories and extended attributes to be
              created with a name not allowed by windows, because

                     - it contains some not allowed character,
                     - or the last character is a space or a dot,
                     - or the name is reserved.

              The forbidden characters are the nine characters " * / : < >  ?  \  |
              and  those  whose  code is less than 0x20, and the reserved names are
              CON, PRN, AUX, NUL, COM1..COM9, LPT1..LPT9, with no  suffix  or  fol&#8208;
              lowed by a dot.

              Existing such files can still be read (and renamed).
```
too.

---

### Post by jokichaki on 2021-08-11
Thanks guys It helps me a lot

---

