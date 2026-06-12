---
title: "Access Ubuntu"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by P13808 on 2008-09-15
Is there a way to access my Ubuntu Partition while running Windows?
They are on separate internal hard drives.  I didn't use the whole hard drive for ubuntu when I partitioned it.  From windows it looks like the hard drive just lost size, partition is invisible, but it shows some ubuntu recycler files.

---

### Post by k33bz on 2008-09-15
> **P13808 said:**
> Is there a way to access my Ubuntu Partition while running Windows?
They are on separate internal hard drives.  I didn't use the whole hard drive for ubuntu when I partitioned it.  From windows it looks like the hard drive just lost size, partition is invisible, but it shows some ubuntu recycler files.


Yes you can access your Linux HDD from windows. But you have to install a program on your windows partition to be able to access it. Give me a few, and I am sure I can find it for you. Or maybe someone will beat me to it.,

---

### Post by Bucky Ball on 2008-09-15
?

You mean you can´t boot into ubuntu from a login screen when you start your machine? Just boots into Windoze?

---

### Post by sisco311 on 2008-09-15
> **P13808 said:**
> Is there a way to access my Ubuntu Partition while running Windows?
They are on separate internal hard drives.  I didn't use the whole hard drive for ubuntu when I partitioned it.  From windows it looks like the hard drive just lost size, partition is invisible, but it shows some ubuntu recycler files.
[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by k33bz on 2008-09-15
[explore2fs]("http://www.chrysocome.net/explore2fs") this one you can use to access your ubuntu while in windows.

[winscp]("http://winscp.net/eng/index.php") this one works over a network. not with dual boot.

---

### Post by northern lights on 2008-09-15
To fist of all "see" the entire disk's content in native Windows, select the "Run" dialog from the Start menu. Type 'mmc' and hit Enter. Form the "File" menu, select "Add/Remove Snap-In..." and add "Disk Management". Now, in the left-hand column, highlight Disk Management. In the right-hand column, you're hdd(s) with graphical partition representations will appear.

In order to read/write from ext3/ext2/JFS/Reiser partitions you need third party software.

You might want to check out [http://www.fs-driver.org/]("http://www.fs-driver.org/")
[http://tombuntu.com/index.php/2008/03/19/four-applications-for-accessing-ext3-partitions-from-windows/]("http://tombuntu.com/index.php/2008/03/19/four-applications-for-accessing-ext3-partitions-from-windows/")
[http://linuxhelp.blogspot.com/2007/03/mount-ext2-or-ext3-partition-in-windows.html]("http://linuxhelp.blogspot.com/2007/03/mount-ext2-or-ext3-partition-in-windows.html")
[http://gentoo-wiki.com/Ext3_in_windows]("http://gentoo-wiki.com/Ext3_in_windows")
[http://www.go2linux.org/accessing-linux-drive-ext-with-vista]("http://www.go2linux.org/accessing-linux-drive-ext-with-vista")

---

### Post by tollboy on 2008-09-15
chaeck this page 
[http://www.codejacked.com/automatically-mount-your-linux-partition-in-windows/](http://www.codejacked.com/automatically-mount-your-linux-partition-in-windows/)
there are many other utilities for accesing linux partition 
but be aware, dont delete any configuration file by mistake 
other wise ur ubuntu will be screwed.


u can find other same kind of utilities in google

---

