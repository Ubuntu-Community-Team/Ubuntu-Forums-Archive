---
title: "change mount point"
date: 2013-04-26
forum: New to Ubuntu
---

### Post by reubes85 on 2013-04-26
Hi everyone new to linux, and have just done a fresh install of windows 7 and ubuntu 12.04

I have a few partitions including 50gb windows, 50gb linux, and most of the rest as storage for documents music etc that both OS's can access.

I was trying to go by the tutorials on the internet, and got the ntfs (storage) to mount at bootup, and I did go through the process of changing the locations of the documents pictures to go to my respected storage folders and that worked until I restarted the computer, I tried to alter fstab but all I have seemed to have been able to do is delete all the links that apear in the left panel in Nautilus, if i click on home it still links to the original mount point.

please be kind and explain what outputs from terminal you would like so that you can help me thanks :)

------------------------------------------------------------------------------------------------------------------
sudo fdisk -l

Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000799f5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   102397951    51095552    7  HPFS/NTFS/exFAT
/dev/sda3       102398310   204796619    51199155   83  Linux
/dev/sda4       204796620  1250258624   522731002+   7  HPFS/NTFS/exFAT

----------------------------------------------------------------------------------------------------------------------------------

sudo blkid
/dev/sda1: LABEL="System Reserved" UUID="8C44AF5F44AF4AB2" TYPE="ntfs" 
/dev/sda2: UUID="2A82B3F582B3C39B" TYPE="ntfs" 
/dev/sda3: UUID="88d0dd88-6031-4073-a9c6-c488c42d5664" TYPE="ext4" 
/dev/sda4: LABEL="Storage" UUID="7EBC992759DC4D93" TYPE="ntfs" 

--------------------------------------------------------------------------------------------------------------------------
storage (where I want my home folder to link into (share documents with windows)
so from above I know that storage = UUID is 7EBC992759DC4D93 and is sda4
sda2 = windows
sda3= ubuntu

---

### Post by reubes85 on 2013-04-28
anyone able to help surely?

---

### Post by ibjsb4 on 2013-04-28
Maybe

[https://apps.ubuntu.com/cat/applications/pysdm/](https://apps.ubuntu.com/cat/applications/pysdm/)

---

### Post by dawbomb on 2013-04-28
Do your partitions/drives all mount successfully?

---

### Post by Morbius1 on 2013-04-28
> I was trying to go by the tutorials on the internet, and got the ntfs (storage) to mount at bootup ... 
The only thing missing from your original post is how exactly you did this. Posting the output of the following command will provide that information:
```
cat /etc/fstab
```
> ... and I did go through the process of changing the locations of the  documents pictures to go to my respected storage folders and that worked  until I restarted the computer
There's a number of ways to do this so which one did you choose?

There are a couple of classic ways to do this. One way is to use symbolic links. I don't much care for this method - in fact I don't much like symlinks in general so I'll show you the other way:

Let's say your "Storage" partition is mounted by this expression in fstab:
```
UUID=7EBC992759DC4D93 /mnt/Storage ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
```
And let's say you want /home/reubes85/Documents to point to /mnt/Storage/Documents.

You would use "bind" to connect one folder to the other by adding another line in fstab after all the others that looks like this:
```
/mnt/Storage/Documents /home/reubes85/Documents auto bind 0 0
```
After adding the line to fstab run the following command to test for syntax errors and mount using the new fstab entries:
```
sudo mount -a
```
It will either come back with errors ( bad ) or come back to the prompt which means it mounted it correctly.

---

