---
title: "is a fat32 shared partition needed for ubuntu and xp to access data?"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by dadarkside on 2008-07-27
i recently installed ubuntu on same hard drive as xp.

when i try to access files on my windows partition from ubuntu, the read/write time is really slow.  for example, if im trying to watch a .avi or .mpeg (stored on the ntfs partition) the play rate of the video is slow i would measure the fps to be about 3-4

does ubuntu have a hard time interperting the ntfs file system and i need a fat32 parition also, or is there something else going on here that i dont know about.


fyi, i have a second hardrive installed which has ntfs file system and i have the same problem

---

### Post by halitech on 2008-07-27
reading and writting from NTFS drives can be flaky and from what I've seen on my external drive, it is slower. FAT32 is better supported for now and may be faster. Copying it to an EXT3 drive or folder should be the fastest

---

### Post by cariboo on 2008-07-27
You might want to install ntfs-config, it may help with the problems you are experiencing. Ntfs-config is available either through Add/Remove programs or Synaptic Package Manager.

Jim

---

### Post by dadarkside on 2008-07-27
thanx for the input guys

i've found out the problem... believe it or not, it was a video card driver issue.

---

