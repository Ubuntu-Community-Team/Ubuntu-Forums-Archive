---
title: "Should I format to ext2 on Windows XP"
date: 2008-12-14
forum: Other OS Talk
---

### Post by u-slayer on 2008-12-14
I'm tired of having to constantly defrag my windows partitions to get games to run with freezing. I read that you can reformat a partition to ext2 on windows.

How well does this work? Is it generally faster than NTFS? Has anyone here tried it?

---

### Post by stefangr1 on 2008-12-14
No, I think thats not possible. The ext2 driver aims at sharing files, like the ntfs read/write functionality in Linux.

---

### Post by mips on 2008-12-14
It's not possible to install windows on anything but FAT&NTFS formatted partitions. You heard wrong.

---

### Post by u-slayer on 2008-12-14
> **mips said:**
> It's not possible to install windows on anything but FAT&NTFS formatted partitions. You heard wrong.

I'm not trying to install windows. 

I have windows on Drive C and a games partition on Drive D. I want to reformat Drive D to ext2.

---

### Post by albinootje on 2008-12-14
Ext2 is the "old default" filesystem for Linux. 
The successor of Ext2 is Ext3, which is a journaling filesystem (that can sometimes make a huge difference when using it in other Operating Systems.)

In MS-Windows there are a few options to read/write to Ext2 or Ext3 partitions, but i'm not sure that there's a transparent solution to be used for gaming in Windows.

But take a look at this :
[http://www.howtoforge.com/access-linux-partitions-from-windows](http://www.howtoforge.com/access-linux-partitions-from-windows)
and see for yourself.

---

### Post by eldragon on 2008-12-14
dont do it if its a dedicated windows partition, since windows wont be able to fsck the partition in the event of a dirty shutdown...

if you plan to share the partition with a linux install, then i would definately consider it.

---

### Post by mips on 2008-12-15
> **u-slayer said:**
> I'm not trying to install windows. 

I have windows on Drive C and a games partition on Drive D. I want to reformat Drive D to ext2.

In that case it can be done but I find it slower than ntfs. There are also issues if something should go wrong like not unmounting the filesystem properly etc.

---

### Post by HermanAB on 2008-12-16
The best filesystem for Windows is NTFS - sorry...

---

### Post by mips on 2008-12-16
> **hermanab said:**
> the best filesystem for windows is ntfs - sorry...

+1

---

