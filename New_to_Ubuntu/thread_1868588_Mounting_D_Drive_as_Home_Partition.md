---
title: "Mounting D:\ Drive as Home Partition"
date: 2011-10-24
forum: New to Ubuntu
---

### Post by Moofu on 2011-10-24
I'm currently Dual Booting Windows 7 Starter and Ubuntu 10.10 Netbook Remix on my eee pc 1005pe.

I've been using the D to store all my personal files (Docs, Music, Photos) so that I can access them from both OS's. Recently I have discovered the advantages of creating a separate partition for home as opposed to having it as a folder. 

My question is would formatting the D drive and then setting it as \home cause any problems in windows? Do I even need to format it?

---

### Post by WasMeHere on 2011-10-24
I would not recommend that, because your home folder is not only storing your documents and media files, but also several configuration files and folders for application programs. These files and folders may need the linux specific access modes that do not work with NTFS (the file system of Windows).

Instead you can use a separate ***data*** partition (with the NTFS file system) where you store documents and media files that you want to access from both Windows and Ubuntu.

Have fun finding out about Ubuntu :-)
Olle

*Edit: You can add symbolic links in your home directories of Windows and Ubuntu to your **data** partition or its directories. This will give you rapid access from both systems.*

---

### Post by ArgusVision on 2011-10-24
This thread might help. [http://ubuntuforums.org/showthread.php?t=1865750](http://ubuntuforums.org/showthread.php?t=1865750)

Also make sure you do a good search prior to posting. I realatively certain there's some more good material out there conserning this.

---

### Post by Moofu on 2011-10-24
What if it was FAT32 instead of NTFS? Would I still run into the same problem?

Thanks for the fast reply btw!

---

### Post by WasMeHere on 2011-10-24
FAT32 would be better for linux, but it is old and limited in many ways. I would *not* recommend it for this purpose.

---

### Post by Moofu on 2011-10-24
Thanks to both of you for the info :)

---

