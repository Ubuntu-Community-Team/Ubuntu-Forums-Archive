---
title: "Enlabling File Creation to an User"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by AeroCross on 2008-05-15
Hello all. I'm having a doubt here. I was happily editing and moving some files in my home folder (/home/aerocross) and everything was great. I was moving and extracting some files and I had to move em to my 2nd Hard Drive (sda1), but now, when it's there, I don't have any permissions to write files, yet, I can move or rename files. I know I can sudo nautilus so I can edit files, but it basically deactivates the GTK themes, and I have to go back again to the root folder, and that pretty much sucks. There's a way I can enlable writing permissions to an user, to my hard drive? My HDD is an NTFS partition,and I already have installed NTFS-3G. I'm using Ubuntu 7.10. Any ideas?

BTW, I'm pro-GUI user, I can extract by Terminal... But what's the point? It should be easier.

---

### Post by Inxsible on 2008-05-15
> **AeroCross said:**
>  I don't have any permissions to write files, yet, I can move or rename files. If you can rename files...you do have write permissions on the drive. Also given that its an NTFS drive, using chown or chmod will not help.

Please make sure that the drive is not full...or you may want to empty the recycle bin and defrag the drive just to see how much space you have on it.

---

### Post by AeroCross on 2008-05-15
Drive's not full (60 GB free).
Drive's not fragmented (99% of non-fragmentation according to PerfectDisk 2008)

I can rename files, even move, copy, or delete files. I can't extract files, I have an Acced Denied, I don't have enough permissions when I try to "extract here" with Ark.

---

