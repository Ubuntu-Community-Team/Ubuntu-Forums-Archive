---
title: "Multiple hard drives"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by fortguy on 2008-05-05
I'm looking forward to installing Ubuntu on my computer as a dual boot system. My computer has two hard drives, each with 298 GBytes. The first drive has a 9.51 GByte factory image Windows Vista recovery partition and a Windows partition with 228 GBytes free space. The second drive is not partitioned and is nearly entirely free. It only contains a recycle bin and a system volume information folder that Windows seems to drop everywhere for indexing searches. I intend to install Ext2IFS so Windows can share files with Ubuntu.

My question is this: Is it better to install Ubuntu to the same drive as Windows and leave the empty drive for sharing files? Would it be better to place the swap, root, and home partitions to a different drive than the Ubuntu installation partition? I realize that using programs and data on different drives can speed things up a little since information on both drives can be read at the same time.

Also, with such generous free space, what would be recommended sizes for each partition, including Windows? My system has 3 GBytes RAM and I'm only using about 60 GBytes drive space between Vista and my own files.

Thank you

---

### Post by glennric on 2008-05-05
It doesn't matter where you put things.  I always put windows on one drive and linux on another.  I recommend making a separate partition for /home and / (the root partition).  Make sure the root partition has about 10 gigs and your home partition has enough for whatever you want to put in it.  For your swap partition 500 MB is probably enough, but if you want to be able to hibernate you will need more (at least as much as your physical memory, unless you use uswsusp and then not quite as much).  
I hope this helps.

Edit:  By the way, you don't need a sharing partition.  That is pretty much a thing of the past since linux can read/write windows partitions and vice versa.

---

### Post by fortguy on 2008-05-06
Would I be able to keep the Windows pagefile on the same swap partition? Also, I'm thinking that, if I wanted to image my future Ubuntu installation, I would want to do that to the other drive in case one drive fails. 

Basically, what you're saying is to provide enough space for Ubuntu and the swap, and then if I want I could fill the rest of the drive with /home?

---

