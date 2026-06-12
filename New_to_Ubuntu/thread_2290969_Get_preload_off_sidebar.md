---
title: "Get preload off sidebar"
date: 2015-08-17
forum: New to Ubuntu
---

### Post by rccharles on 2015-08-17
I installed Ubuntu 14.04 LTS.  There is an icon for the Preload disk.  It looks something like a harddrive icon.  How to I get it out of the sidebar?  What is it anyway?  I tried dragging it to the trash can, but it didn't take.

Robert
PS. Changed to the release number.

---

### Post by dino99 on 2015-08-17
[http://fridge.ubuntu.com/2015/07/03/ubuntu-14-10-utopic-unicorn-reaches-end-of-life-on-july-23-2015/](http://fridge.ubuntu.com/2015/07/03/ubuntu-14-10-utopic-unicorn-reaches-end-of-life-on-july-23-2015/)

---

### Post by rccharles on 2015-08-17
Got the wrong release.  Running 14.04 LTS.

---

### Post by rccharles on 2015-08-17
Found out some more info.  This is a dual boot Ubuntu 10.04 lts and windows xp.  The preload disk is windows xp.  The question becomes how do I avoid mounting the windows xp partition.  Interesting enough, there is a another dos partition and the dos partition isn't mounted.

I have these partitions: ntfs, dos, ext4, and swap. Curiously, the mount command showed the /dos partition mounted, but not in the side bar.  The mount command not did show the ntfs ( windows sp ) partition,  but it's in the sidebar. 

Robert

---

### Post by grahammechanical on 2015-08-17
The Launcher will show an icon for each partition. The icon looks like a hard disk drive. Have you tried right clicking the icon and selecting Unlock from Launcher? Put a DVD disc in the DVD drive and an icon for it will appear in the Launcher. Liewise, for a USB memory stick.

---

### Post by rccharles on 2015-08-17
That did it.  Thanks.

Don't really understand why ubuntu is displaying the partitions this way.  What are the rules?

I have these partitions: ntfs, dos, ext4, and swap. Curiously, the mount command showed the /dos partition mounted, but not in the side bar. The mount command not did show the ntfs ( windows sp ) partition, but it **was** in the sidebar until I told it to go away. I assume when I define a partition, it will put the correct filesystem on the partition.  I have not put any data in the dos partition.

---

