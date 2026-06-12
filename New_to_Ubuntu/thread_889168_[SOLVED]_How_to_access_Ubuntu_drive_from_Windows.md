---
title: "[SOLVED] How to access Ubuntu drive from Windows"
date: 2008-08-13
forum: New to Ubuntu
---

### Post by discmaster on 2008-08-13
I have win xp installed on an PATA drive, IDE1. I also have 2 SATA drives on this system. 1 is storage, & 1 is a previous Ubuntu installation. When I go into "My Computer", I am unable to view the SATA drive w/ the linux install. 

That drive is also partitioned with storage on it as well. Can anyone tell me why that drive won't show up unless I use a pgm. like explore2fs? 

Is there a program to install on windows that will allow me full access to that linux drive, so I am able to get to the other partitions?

Thanks! :popcorn:

---

### Post by halitech on 2008-08-13
the reason that Windows can't see the SATA drive with the Ubuntu install is because Windows doesn't know how to read the EXT3 (I'm assuming) file system that Ubuntu normally uses. You will either need to use a program that can read it or boot from a live cd and copy the files to a thumbdrive so you can get at them.

---

### Post by alienexplorers on 2008-08-13
You could try ext2ifs (not sure of the name, but thats pretty close).  I have used this program since 2006 and it has never let me down.  It is easy to setup and assigns drive letters to your partitions.

---

### Post by iaculallad on 2008-08-13
You might be needing the software from the site below in order for you to access Ext2/Ext3 formatted drives in windoze:

> [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by deathvalleyjoker on 2008-08-13
[http://www.fs-driver.org/download.html](http://www.fs-driver.org/download.html)

this is the same site but with a direct link to the download page. i jsut used it the other day and i have a set up like yours. it worked very easily. and it was cool bc it let you pick the drive letter, so naturally i picked U:\ for Ubuntu. 

so jsut go into your xp partition, download this, and then run it from wihtin windows. after its done you will be able to read all of your linux partition.

welcome to the community & cheers.

---

### Post by discmaster on 2008-08-13
All good suggestions, guys. I was looking for the simplest solution, & for me it seems to be the pgm. that **iaculallad **& **deathvalleyjoker** suggested. I downloaded it & it worked like a charm. 

Thanks!

---

