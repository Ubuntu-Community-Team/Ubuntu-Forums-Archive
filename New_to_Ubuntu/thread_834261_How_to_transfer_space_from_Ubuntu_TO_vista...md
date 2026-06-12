---
title: "How to transfer space from Ubuntu TO vista..??"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by higatech on 2008-06-19
hi 
By mistake i made a wrong partition 26gb for vista and 200gb for ubuntu ....

Plzz tell a way out so can I transfer some space to VIsta...

---

### Post by cdtech on 2008-06-19
I've used gparted to arrange my partitions. You could use gparted to shrink your ext file system then go into Vista and reallocate your Windows partition.

---

### Post by webofunni on 2008-06-19
Hi,

  You need to use any partition editor such as GParted < [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/) > to edit the partition table. 

  You can Splt/Join partitions using that. 

Regards,
Unni

---

### Post by housam on 2008-06-19
As advised above , you've to boot from Gparted live cd to resize your partitions . Be aware that it'll take a long time to move ubuntu to the backward if it is laying behind the windows partition.

---

### Post by fatality_uk on 2008-06-19
If you go here, you can download the livecd and use that as housam suggested
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by kansasnoob on 2008-06-19
> **cdtech said:**
> I've used gparted to arrange my partitions. You could use gparted to shrink your ext file system then go into Vista and reallocate your Windows partition.

Cdtech is exactly right. You'll first want to "shrink" the Ubuntu partition using Gparted, but then you'll want to use Vista's own tools to expand Vista.

This gives you some idea what Vista's "tools" look like:

[http://vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista/](http://vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista/)

---

