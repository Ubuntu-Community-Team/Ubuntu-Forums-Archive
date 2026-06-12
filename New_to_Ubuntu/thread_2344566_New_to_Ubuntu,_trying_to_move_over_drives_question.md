---
title: "New to Ubuntu, trying to move over drives question"
date: 2016-11-26
forum: New to Ubuntu
---

### Post by avsrock78 on 2016-11-26
So my old Windows 10 PC appears to be dead, from what I suspect was a bad update that locked the boot drive (SSD). I've given up trying to unlock it and have gone out and purchase a new small SSD and installed Ubuntu 16.04. It's up and running, seems stable, but I cannot figure out how to see my old 2 x 3TB Sata 3 hard drives that were being used for data only on my Windows 10 machine. 

When I ran the lsblk command I see they are both present as sdb and sdc respectively:
NAME                  MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda                     8:0    0 111.8G  0 disk 
&#9500;&#9472;sda1                  8:1    0   487M  0 part /boot
&#9500;&#9472;sda2                  8:2    0     1K  0 part 
&#9492;&#9472;sda5                  8:5    0 111.3G  0 part 
  &#9500;&#9472;ubuntu--vg-root   252:0    0  95.3G  0 lvm  /
  &#9492;&#9472;ubuntu--vg-swap_1 252:1    0    16G  0 lvm  [SWAP]
sdb                     8:16   0   2.7T  0 disk 
&#9500;&#9472;sdb1                  8:17   0     1M  0 part 
&#9500;&#9472;sdb2                  8:18   0   127M  0 part 
&#9492;&#9472;sdb3                  8:19   0   2.7T  0 part 
sdc                     8:32   0   2.7T  0 disk 
&#9500;&#9472;sdc1                  8:33   0     1M  0 part 
&#9500;&#9472;sdc2                  8:34   0   127M  0 part 
&#9492;&#9472;sdc3                  8:35   0   2.7T  0 part 
sr0                    11:0    1  1024M  0 rom 

My question is how do I actually view the data? Yes I am so ingrained in windows I still think of simple windows file system so any help would be appreciated.

---

### Post by Mark Phelps on 2016-11-26
Sorry, but most likely, you will NOT be able to retrieve the data from the old Win10 drives.

Why?

Because, Win10, be default, implements a new hibernation method known as FastStartup, NOT to be confused with Fast Boot.  Using this method, Windows keeps its drives mounted, even when not running.  This prevents Linux distros from mounting those drives.

---

### Post by oldrocker99 on 2016-11-26
> **Mark Phelps said:**
> Sorry, but most likely, you will NOT be able to retrieve the data from the old Win10 drives.

Why?

Because, Win10, be default, implements a new hibernation method known as FastStartup, NOT to be confused with Fast Boot.  Using this method, Windows keeps its drives mounted, even when not running.  This prevents Linux distros from mounting those drives.

And, once again, Microsoft shows its "love" for alternate operating systems. Feh.

---

### Post by avsrock78 on 2016-11-26
Ugh, great. Guess I'll have to put them in another old machine and get the data off them then migrate them over.

---

### Post by deadflowr on 2016-11-26
You should have a Windows recovery disk. (Should is the optimal word)
you can also use the installation media to recover it, too.
You can use that to recover the busted boot loader and then re-access the Windows install.

But that's my practical sense, as I haven't needed to ever use it, so.. (Take it with a chunk of salt)

From there, you can unset the fast start option.
Which will allow you to do whatever you want with the disk.
[Turn fast start on or off]("http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html")

---

### Post by oldfred on 2016-11-26
Default Linux mount of NTFS is read/write. But when hibernated (the fast start up) or needs chkdsk if possible corruption the Linux driver will not mount it.

But you may (may or only possibly) mount read only.

 Read only mount of Windows may work if corrupted or hibernated
sudo mkdir /mnt/win
sudo mount -o ro /dev/sdb# /mnt/win
sudo nautilus /mnt/win 

You can adjust for each drive & partition, if it works on one.

---

### Post by timfinley on 2016-11-27
Mark Phelps:

Is there a way to disable that FastStartup? I wasn't aware of that and have Win10 on a separate partition. Having read this reply makes me a little nervous about the data stored on the Windows side.

---

### Post by oldfred on 2016-11-27
Fast Start up off (always on hibernation) See post by Mark here:
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

---

### Post by timfinley on 2016-11-27
Thank you oldfred.

---

