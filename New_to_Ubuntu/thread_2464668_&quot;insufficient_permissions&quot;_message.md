---
title: "&quot;insufficient permissions&quot; message"
date: 2021-07-08
forum: New to Ubuntu
---

### Post by rtroxel2 on 2021-07-08
Hi, everyone,

I recently installed a hard drive from my old Windows PC to my new Ubuntu 20.04 PC. Consequently, the Ubuntu OS is on one hard drive, while my data is on the second hard drive. However, when I tried to download data from the net to the 2nd hard drive, I received the message: "insufficient permissions".

How do I add the permissions?

Thank you,

Roy

---

### Post by TheFu on 2021-07-08
How to properly mount storage depends on the file system involved.  What file system is being used?

Also, if the drive was used in Windows previously, it may not have "closed" the file system correctly.  Windows versions since Win8 haven't handled properly closing file systems in an effort to make Windows appear faster.  This breaks the expected functionality when we'd like another OS to mount the storage. If it is mounted and you can see the files, it could be read-only mounted as a way to protect the files from corruption.

What file system is being used?

---

### Post by rtroxel2 on 2021-07-09
TheFu,

The file system for the Ubuntu 20.04 hard drive is standard ext4. The file system for the Windows data drive is something called "fuse", but I've only heard of Windows using  NTFS or FAT32. It's my understanding that Ubuntu can read those two also.

I haven't used Ubuntu for a couple of years, but I remember you could add the "write" property to a disk or file using the chmod command. Has that changed?

Thanks again,

Roy

---

### Post by TheFu on 2021-07-09
> **rtroxel2 said:**
> TheFu,

The file system for the Ubuntu 20.04 hard drive is standard ext4. The file system for the Windows data drive is something called "fuse", but I've only heard of Windows using  NTFS or FAT32. It's my understanding that Ubuntu can read those two also.

I haven't used Ubuntu for a couple of years, but I remember you could add the "write" property to a disk or file using the chmod command. Has that changed?

chmod doesn't work on NTFS.
fuse almost always means a non-native file system. If you can, changing it to native would be best. You'll get better performance and control of all the normal Unix/POSIX permissions.  Alas, swapping a file system means wiping the partition completely. Best to do that BEFORE you have lots of stuff on in.  The downside to changing to a native Linux file system is that Windows can't read it.  I see that as a positive.  

I have only 1 HDD that gets used to move data physically between Windows and Linux.  Of course, using the network to move things is pretty easy. I use that most of the time.  That physical NTFS drive is only used because my video recording hardware will only write to NTFS file systems. It's a hardware limitation, so I'm stuck with it.

Ok, so back to the problem.  NTFS permissions, owner and group settings are control at mount time and cannot be changed without remounting. This is the Linux way of tricking the file system into working as needed for Linux use. The minimum commands to mount non-native file systems:
```

# Non-native file systems - ntfs, exfat, fat32
sudo mkdir /media/canon
sudo mount -t auto -o uid=$USER /dev/sdb1 /media/canon
 
# When done
sudo umount /media/canon
```

But those just get the job done and aren't very efficient.
The options can be more than just the uid.  Options to be swapped into the mount command:
```
# exfat
  -o dirsync,nodev,windows_names,nosuid,noatime,async,timeout=2,uid=1000,gid=1009,fmask=0002,dmask=0002

# ntfs - big_writes helps performance upto 30%
  -o nodev,permissions,windows_names,nosuid,noatime,async,big_writes,timeout=2,uid=1000,gid=1009,fmask=0002,dmask=0002
```

You'll need to correct the uid and gid settings for your username.  Use the '**id**' command to determine those. They are NOT what I've put above.
Mount options cannot have any spaces, so don't accidentally add some. That changes the entire meaning of the line.
* Use 'id' to see the uid and gid numbers for your userid.
* If multiple users need write access, choose a shared group. You might need to create this shared Unix group.
* NTFS performance - async,big_writes
* exFAT performance - dirsync in kernel-based exfat mount code.
* uid=????   where ???? can be either the number or the text.

For ext2/3/4 or any native Linux, use these options for "data" :
```
# ext4 - nofail for data-only mounts
  -o nodev,nosuid,noatime,errors=remount-ro,nofail

```

---

### Post by rtroxel2 on 2021-07-09
Thanks, again!

Roy

---

### Post by TheFu on 2021-07-09
The mount stuff can be put into the /etc/fstab file. Follow the pattern for existing examples.  Instead of using /dev/sdb1, use the UUID=xxxx-xxxxx-xxxxx-xxxxx or LABEL="whatever-label-you-gave-it" in that place of the comment or fstab.

For native Linux file systems, chmod and chown work.  There are lots of tutorials for those.  Once you change the owner, it will always have that owner on the next mount.   An example /etc/fstab mount line:
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
UUID=e3396778-bf33-42f5-8420-d1a31bdac7df   /stuff   ext4    nodev,nosuid,noatime,errors=remount-ro,nofail     0  1
```

---

### Post by TheFu on 2021-07-09
Get the UUID for any partition using the '**blkid**' command.
I prefer to use a LABEL, since humans get to make the LABEL and we can put something useful as the value.  DO NOT PUT SPACES IN THE LABEL.
```
LABEL=250G   /stuff   ext4    nodev,nosuid,noatime,errors=remount-ro,nofail     0  1
```

---

### Post by Impavidus on 2021-07-09
> **rtroxel2 said:**
> 
The file system for the Ubuntu 20.04 hard drive is standard ext4. The file system for the Windows data drive is something called "fuse", but I've only heard of Windows using  NTFS or FAT32. It's my understanding that Ubuntu can read those two also.
**fuse** doesn't refer to the filesystem, but to the method for mounting it. It's probably NTFS. Ubuntu can read and write NTFS, but if the filesystem is damaged or not properly closed after last use (and Windows 8 and up typically don't properly close filesystems on internal drives after use), Ubuntu may have read-only access or no access at all. And Ubuntu cannot fix NTFS. That's something you have to do on Windows. For an internal harddrive in a Linux-only computer, it's best to avoid NTFS and use native Linux filesystems only. You can't convert it, so you have to copy all files to a backup drive, format to a Linux native filesystem and restore your backups.

---

