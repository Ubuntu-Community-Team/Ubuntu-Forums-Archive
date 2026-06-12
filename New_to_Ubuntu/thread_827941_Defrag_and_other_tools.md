---
title: "Defrag and other tools"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by Tim Silver on 2008-06-13
Hi,

Being a complete beginner to any form of Linux, I notice the absence of disk management utilities such as Defrag etc. Is that because the way Linux writes to disk is better structured?

I have downloaded this file -  [http://tldp.org/LDP/Linux-Filesystem...-Hierarchy.pdf](http://tldp.org/LDP/Linux-Filesystem...-Hierarchy.pdf), but that's my weekend reading!

---

### Post by argail1980 on 2008-06-13
I never bothered defragging any disk since I don't know when. There is fsck and it's variants for checking for errors (command line tools). But u don't want to use it unless you know what you're doing, or have a crash.

By default, ubuntu will check your disks every month or so anyway.

---

### Post by Rocket2DMn on 2008-06-13
The ext3 filesystem does not get fragmented like NTFS and FAT32 systems do, so a defragmenter is not needed.  If you have attached FAT32 or NTFS drives, you need to defrag them from a Windows computer (or from Windows in your dual boot).

---

### Post by Joeb454 on 2008-06-13
> **Rocket2DMn said:**
> The ext3 filesystem does not get fragmented like NTFS and FAT32 systems do, so a defragmenter is not needed.

I heard it *can* get fragmented (however unlikely) though even then it is the smallest amount that you need not worry about it.

I'm not sure of the truth in it though :)

---

### Post by Rocket2DMn on 2008-06-13
Yes, every file system can get fragmented to an extent over time, ext3 is just much more resistant to it because of the way it saves data to the hard disks.  I have heard that the next generation of the Extended File System, ext4, will have a defrag tool.

---

### Post by hyper_ch on 2008-06-13
it will get fragemnted when you're constantly running low of space... bascially when you want to save a file that is bigger than the biggst chunke of continuous free space.... general rule: if you have 10% or free diskspace then you wont need to defrag and the system automagically regulates itself.

---

