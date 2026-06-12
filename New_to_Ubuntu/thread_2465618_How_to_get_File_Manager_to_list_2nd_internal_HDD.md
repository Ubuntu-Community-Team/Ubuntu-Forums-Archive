---
title: "How to get File Manager to list 2nd internal HDD"
date: 2021-08-06
forum: New to Ubuntu
---

### Post by mumbletypeg on 2021-08-06
(Computer) shows my 2nd internal hard drive, but my (File Manager) does not show it. How do I get File Manager to list it? 
Simply want easy access to the files on it.

---

### Post by ActionParsnip on 2021-08-06
Mount the file system. If the partition is on an internal disk and will always need to be accessed then you can add its mount in /etc/fstab and it will mount at boot.

---

### Post by Impavidus on 2021-08-06
If the file manager can mount the second hard drive (or rather, the filesystem present there), it should be listed, which is not the case. Maybe the filemanager doesn't understand the partitioning or the filesystem. What does```
sudo parted -l
```tell?

On the other hand, if it's already mounted via /etc/fstab, the filemanager won't show the hard drive in the list, but its contents can be browsed simply by navigating to the mountpoint.

---

### Post by GhX6GZMB on 2021-08-06
I think a "Windows mindset" is in play here, and the OP expects to see C:, D: etc. UNIX/Linux doesn't work that way.

---

### Post by mumbletypeg on 2021-08-08
> **ActionParsnip said:**
> Mount the file system. If the partition is on an internal disk and will always need to be accessed then you can add its mount in /etc/fstab and it will mount at boot.

I tried to mount the drive using the commands in the editor and when trying to reboot it froze. So I started a new thread titles: “installed, rebooted, stuck on boot screen”

Mi914: You are correct about my windows mindset.

---

### Post by TheFu on 2021-08-09
On Unix, there are different file systems. How to mount a file system depends on which file system it is.  We need to know that and some other information before we can help.

[Https://ubuntuforums.org/showthread.php?t=2464944&p=14048909#post14048909](Https://ubuntuforums.org/showthread.php?t=2464944&p=14048909#post14048909)
Beware that using NTFS will place constraints on the use of the storage for that second disk. Also, the entire disk shouldn't be mounted, but a partition on it.  Always ensure there is at least 1 partition with a file system on any disks.  The "C: drive" and "D: drive" terms are factually incorrect. MSFT tried to keep it simple for normal people. C: and D: are partitions, probably with NTFS as the file system.

Unix doesn't force names like C/D/E/F/ .... Z onto storage to be mounted.  Mounts can be anywhere, just create an empty directory. This will be a "mount point" to connect the mounted file system onto.  Don't mount storage under your HOME directory. That will make backing up data harder in the future. If you don't know where to put a new mount for an internal HDD, use a directory like /Data/{something}.  If you create a label for the partition, then that will be used by automatic mounting tools. **gparted** can be used to put a LABEL onto a partition.  gparted is the most complete disk setup/management tool for Linux. Unfortunately, it does everything except it won't mount storage.  The best way to mount storage is through the fstab config file, as my link above explains.

---

