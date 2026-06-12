---
title: "[SOLVED] Defrag Cross-Platform FAT32 Flashdrive"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by SurrealWraith on 2008-05-13
I use the same flashdrive on my Ubuntu Box and Windows Box (which I keep only for gaming without taking the time to configure everything with WINE).  While Ubuntu and Linux in general in it's superiority does not require defragmenting of drives, I believe my flashdrive has become fragmented from use with Windows.  Is there anyway to defragment it from Ubuntu, or do I need to do it from Windows?

Thanks.

---

### Post by solitaire on 2008-05-13
I don't thing fragmentation will be a big issue. (it's technically good for the SSD) :D

But I don't know of any Linux Programs that will defrag Fat32 it might be quicker doing it in windows.

---

### Post by HotShotDJ on 2008-05-13
Flashdrives are pretty small.  It would probably be easier (even using Windows) to just copy all the files on it to a directory on your harddrive, delete them from the Flashdrive, and then just copy them back.

---

### Post by SurrealWraith on 2008-05-13
Very true.  Thank for the advice.

---

### Post by JoshuaRL on 2008-05-13
I agree.  And FAT drives will have problems with fragmentation, as will NTFS.  ext3 doesn't have that problem, so the lack of applications for that purpose in Linux.

---

### Post by psusi on 2008-05-15
> **JoshuaRL said:**
> I agree.  And FAT drives will have problems with fragmentation, as will NTFS.  ext3 doesn't have that problem, so the lack of applications for that purpose in Linux.

It isn't an issue with the filesystem, but rather the allocation policies that the OS uses when writing files.  Linux is smarter about where it chooses to place files, so they tend not to get fragmented.  And contrary to popular belief, there has always been a defrag utility for ext2/3 which you can find in the defrag package in the universe repository.

As for fragmentation on a flash drive, it will not cause any performance loss since there is no rotational latency with solid state disks, so my advice is not to worry about it.

---

