---
title: "Partitioning help"
date: 2013-09-10
forum: New to Ubuntu
---

### Post by ka2012 on 2013-09-10
I have a netbook dual-booting windows and ubuntu 12.04. I would like to add a storage partition, to keep music and documents and stuff in, but I have a few questions about the best way to go about it...
 
[ATTACH=CONFIG]246170[/ATTACH]
Here's a screensho of my partitions in gparted...as you can see, windows takes up the first 2, then theres a large unallocated space (I defragmented and shrunk windows), then an extended partition with ubuntu, swap, and windows recovery in it. If I use the space to create a storage partition, should I create a new primary partition (I only have 2 primary and one extended, so there's room for one more with mbr), or should I try to make the extended partition bigger and then make the storage a logical partition? I know I could store documents and music and stuff in the extended partition, but what about applications? Could those be installed there too, or wouldn't that work? Lastly, what file type should I make it? I know ntfs would work for both, but I read somewhere that Fat32 would too, so which would be best for shared files? Thanks in advance for any help

---

### Post by oldfred on 2013-09-10
It does not matter if primary or logical inside the extended. The requirement is that Windows only boots from primary partitions, but it reads and writes NTFS data logical partitions. Linux also reads & writes NTFS partitions.

I do not recommend FAT32 anymore. Many years ago the NTFS driver was new and had a few issues. I converted my FAT32 shared data to NTFS when I installed 10.10, so that was three years ago. I still use that NTFS partition but do not boot XP anymore. (Just have not moved data to Linux data partition yet.)

FAT32 does not have a journal so chkdsk can take forever or not work as well. FAT32 also has a file limit of 4GB, so if you have any large files you cannot store them in a FAT32 partition.

---

### Post by Jonathan Precise on 2013-09-10
> **ka2012 said:**
> I have a netbook dual-booting windows and ubuntu 12.04. I would like to add a storage partition, to keep music and documents and stuff in, but I have a few questions about the best way to go about it...

Here's a screensho of my partitions in gparted...as you can see, windows takes up the first 2, then theres a large unallocated space (I defragmented and shrunk windows), then an extended partition with ubuntu, swap, and windows recovery in it. If I use the space to create a storage partition, should I create a new primary partition (I only have 2 primary and one extended, so there's room for one more with mbr), or should I try to make the extended partition bigger and then make the storage a logical partition? I know I could store documents and music and stuff in the extended partition, but what about applications? Could those be installed there too, or wouldn't that work? Lastly, what file type should I make it? I know ntfs would work for both, but I read somewhere that Fat32 would too, so which would be best for shared files? Thanks in advance for any help

Please, BACKUP EVERYTHING FIRST!!!

Then go to an ubuntu live usb. Start the installer. Choose "something else" for partitioning. Mount your Ubuntu partition as "/". Do not format it!
Then make a new partition (Logical | Fat32/VFat) on the free space. Mount it as /data or as /media.

As for apps, make another logical partition on the remaining "Free space" (Logical | Ext4) mounted as /usr

Note: some apps install in /opt. However, most install in the relevant /usr sub-directory (mostly /usr/bin). Click install. Ignore warnings about removing stuff in /usr /etc ... The installer will try to re-install the programs.

Congratulations! You are DONE!

---

### Post by ka2012 on 2013-09-10
Ok thank you both for your help and getting back so quickly. programs were actually kind of an afterthought, since I dont really have any programs that I absolutely need for both, and the only real things that I use windows for anymore are my games...also, an additional question, if the space is formatted as an ntfs logical partition, would it be possible to run virtual machines using virtualbox in that space?


Jonathan Precise: I'm sorry, I don't really understand what you're saying...I get that the /data is for storage and /usr for apps, but I dont understand, is it reinstalling ubuntu, or just transferring them from the existing install or what? Please clarify... Also, I don't understand why apps would be in the ext4 space...my goal was to see if it was possible to access them using both os's and I am under the impression that windows can't even read ext4 without extra software...

---

### Post by oldfred on 2013-09-10
You cannot run an app in both.

I did have Windows Picasa in XP and installed via Wine Windows Picasa in Ubuntu and had all the same photos in my shared NTFS partition. I also used shared data for Firefox & Thunderbird, but had to install each in each system, just data was shared, so I could read same email from either system and have same bookmarks for Firefox.

---

### Post by Jonathan Precise on 2013-09-11
> **ka2012 said:**
> Jonathan Precise: I'm sorry, I don't really understand what you're saying...I get that the /data is for storage and /usr for apps, but I dont understand, is it reinstalling ubuntu, or just transferring them from the existing install or what? Please clarify...

Actually, use GParted to format the empty space to NTFS. Then add a line in /etc/fstab:

```
UUID=*uuid* /data    ntfs    defaults    0    1
```

Replace *uuid* with the UUID of the partition (find that in GParted as well).

Done!:guitar:

[HR][/HR]Re-installing is a way to do this without having to edit the FStab line. However, if you do this this way, BACKUP FIRST!!!!!!!!!!!!!!!!

---

### Post by ka2012 on 2013-10-06
Ok, finally got back to this, sorry I took a while...I ended up creating a new primary partition for storage with half of the space (30 GB is plenty; I don't really have very much data; I transferred my files and I'm still only using about a tenth of the space), and then I'm going to add the remaining space to my extended partition so I have room to create some logical partitions/other OS's in the future...thanks for the help and suggestions!

---

