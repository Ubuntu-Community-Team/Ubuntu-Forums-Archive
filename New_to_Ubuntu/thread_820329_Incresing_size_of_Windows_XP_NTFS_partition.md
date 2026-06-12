---
title: "Incresing size of Windows XP NTFS partition"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by ShiningWolf on 2008-06-06
How do I increase the size of an Windows NTFS partition. Does not seem that gparted can handle NTFS.  Will the resizing affect the XP installation?

Thanks in advance!

---

### Post by sayakb on 2008-06-06
NTFS has fragmented data and you need to defragment data first. Defragmenting several times will push the data to one side and you would be able to use GParted to resize the partition. Also see: [Parted magic]("http://ubuntuforums.org/partedmagic.com/").

---

### Post by ShiningWolf on 2008-06-06
do I also need to defrag the Kubuntu file system (ext3)?

---

### Post by ShiningWolf on 2008-06-06
do I also need to defrag the Kubuntu file system (ext3)?

---

### Post by sayakb on 2008-06-06
No. ext3 does not get fragmented to great extent. You don't need to defragment ext3 partitions. Read [here]("http://www.whylinuxisbetter.net/items/defragment/index.php").

---

### Post by ShiningWolf on 2008-06-06
What is the ideal way to partition your drive if you share Windows and Linux, e.g. a partition for each OS and a shared data partition or do you just use two, one for each S and data is local to each OS?

Are there any issues with Linux writing/reading from NTFS?

---

### Post by sayakb on 2008-06-06
Linux can perfectly read/write on NTFS partitions.
As for partitioning for Linux, you can create 3 partitions:
/ = max 10GB
/home = Whatever size you want
swap = should be >= size of your RAM

Even you can make Windows read/write on the ext3 partitions by [EXT2IFS driver]("http://www.fs-driver.org/").

---

### Post by Paqman on 2008-06-06
> **LinuxIsInnovation said:**
> 
/ = max 10GB


If you plan to be doing anything that creates really big temp files (like DVD ripping) you might want to make that bigger.

---

### Post by sayakb on 2008-06-06
> **Paqman said:**
> If you plan to be doing anything that creates really big temp files (like DVD ripping) you might want to make that bigger.
You can always set the path of the destination folder where the music shall go. :)

---

### Post by Paqman on 2008-06-07
> **LinuxIsInnovation said:**
> You can always set the path of the destination folder where the music shall go. :)

Sorry, I meant DVD copying, not ripping. Some software is better behaved than others, but in general they all make some pretty stupendously big temp files during the process.

---

