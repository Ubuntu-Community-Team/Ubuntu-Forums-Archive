---
title: "installation problems with Vista"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by plstjj on 2008-06-25
I wonder if anyone can help with the installation problems I am having installing Ubuntu on my new computer running Windows Vista 64bit version. I went through the process suggested on several help sites on the web of creating an unformatted free space on my hard drive using the Disk Management process in Vista, which has created a blank space of about 250Mb. The problem is that when I get to the point of partitioning the drive in ubunto, it does not recognise this blank space & does not give the option "Use the largest continous free space" but only gives two options: one is to partition the whole drive thereby risking destroying Vista & the other is to do a manual install, which I don't understand how to use. If anyone knows how to get around this problem & perform a safe install without destroying Vista, your help would be appreciated.

---

### Post by fiddledd on 2008-06-25
If that 250MB isn't a typo that's not enough space. I'd suggest at least 10GB or more if you have it free. Then try the install again.

---

### Post by plstjj on 2008-06-25
Sorry it's a typo - should be 250Gb

---

### Post by jualin on 2008-06-25
You can install everything by performing a manual install (don't be scared). Back up your data first just in case something goes wrong. 
The basics for the manual partioning process are very simple. You need two partitions for Ubuntu to run. You need a SWAP partition (formatted as SWAP) and you need a Ext3 or Ext2 partition for Ubuntu to install on. The Swap partition is just in case you run out of RAM so you can make this partition 1 GB. The Ext3 partition is going to be your main partition and this one you need select "**/**" as your mount point (right click on the Ext3 partition and Properties). The only tricky part is to make sure that you are not deleting the Windows partition. Make sure you check the free space on each partition since this will tell you which is the Windows Partition. Hope this helps you!

---

### Post by billgoldberg on 2008-06-25
Boot from the live cd, open up "gnome partition manager" (gparted) and format it to a ext3 or reiserfs or something.

The try the install again.

---

