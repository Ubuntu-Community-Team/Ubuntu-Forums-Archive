---
title: "Accessing NTFS Partition"
date: 2013-02-09
forum: New to Ubuntu
---

### Post by dimetri on 2013-02-09
Hi All,

Planned to migrate from Windows to Linux after a long time. Was able to install Ubuntu 12.04 on desktop by removing Win 7. Was able to retain other two partitions in system where all data files were there. 

Just curious to know if there is any harm if i leave the two partitions in NTFS only and access data. Will it cause any problem if i save data directly into that Drive, say if i download anything from Internet can i save directly into that drive rather than saving in Linux and then copying to the drive. 

Thanks in advance.

---

### Post by sudodus on 2013-02-09
It is OK. The linux driver for NTFS is well tested and debugged since several years. Many people (including me) have used NTFS in dual boot systems as data partitions for read/write from Windows as well as from linux.

However, the linux driver for NTFS is a bit slow. So if you have only Ubuntu, it would be a good idea to convert to an (ext3 or) ext4 file system.

You should have an external drive (USB or eSATA) for backup anyway. Use that drive to store your data temporarily(?) while you convert the partitions to ext4!

---

### Post by Mark Phelps on 2013-02-09
The only problem you might have using NTFS, is if the filesystem becomes corrupted, you won't be able to fix it from Ubuntu.  It will require CHKDSK -- which is an MS Windows utility.

That said, I have been using shared NTFS data partitions for years now and never encountered this problem.

However, I did create an Ext4 data partition to be used to share critical data between by various Linux distros.

---

### Post by coetzeec2380 on 2013-02-09
Hi ,

I found there is maybe a program you can use called test disk. 
i a terminal environment , type sudo apt-get install testdisk
after installation simple type testdisk follow the prompts 

regards

---

### Post by sudodus on 2013-02-09
> **coetzeec2380 said:**
> Hi ,

I found there is maybe a program you can use called test disk. 
i a terminal environment , type sudo apt-get install testdisk
after installation simple type testdisk follow the prompts 

regards
Testdisk is a good tool to recover partitions that are damaged. But I don't think dimetri needs that yet ;-) 
I think (s)he can read the NTFS drives.

---

### Post by dimetri on 2013-02-09
Thanks for the info sudodus & Mark Phelps. Will do the backup and convert. I know this sounds a bit dumb on my part but is there a way to convert that NTFS to ext4 without having to take data back (Its kinda boring to sit for hrs to take backup :p). 

I am planning to migrate completely to linux tired of the prob with WIndows. Any user guide available here to linux for home users :D. Mostly to understand how things work and how to easily get around linux since first time migrating from WIndows after  a long time.

---

### Post by sudodus on 2013-02-09
> **dimetri said:**
> Thanks for the info sudodus & Mark Phelps. Will do the backup and convert. I know this sounds a bit dumb on my part but is there a way to convert that NTFS to ext4 without having to take data back (Its kinda boring to sit for hrs to take backup :p). 

No, you need to copy the data, re-format the partitions and copy the data back. But you need not baby-sit the copying. Do it while you sleep or work :-D
> 
I am planning to migrate completely to linux tired of the prob with WIndows. Any user guide available here to linux for home users :D. Mostly to understand how things work and how to easily get around linux since first time migrating from WIndows after  a long time.

You can find many good ***linux tutorials*** on the internet. Look briefly at them and read those that fit your needs!

There are also books (paper books or ebooks), that you might prefer. Search for ***linux books*** on the Internet.

---

### Post by dimetri on 2013-02-10
Duly noted sudodus. Appreciate your inputs for the first post. Googleing my way to linux

---

### Post by oldfred on 2013-02-10
Some links I have saved.

       A master thread on learning/books/terminal/bash/Linux etc
Linux Command Line Learning Resources
[https://help.ubuntu.com/community/CommandLineResources](https://help.ubuntu.com/community/CommandLineResources)
[http://ubuntuforums.org/showthread.php?t=1909108](http://ubuntuforums.org/showthread.php?t=1909108)

   Thread on books:
[http://ubuntuforums.org/showthread.php?t=1874294](http://ubuntuforums.org/showthread.php?t=1874294)

   Ubuntu Documentation:
Official Ubuntu Documentation
[https://help.ubuntu.com/](https://help.ubuntu.com/)
[https://help.ubuntu.com/community](https://help.ubuntu.com/community)
[http://ubuntu-manual.org/](http://ubuntu-manual.org/)
[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

---

