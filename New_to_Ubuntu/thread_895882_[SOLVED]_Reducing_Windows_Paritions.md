---
title: "[SOLVED] Reducing Windows Paritions"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by kjohansen on 2008-08-20
I set up my machine to dual boot.  I gave Vista and Ubuntu equal size partitions (about 50 GB each), thinking I would do equal work in both.  I havent booted windows in a few weeks.  I want to shrink the windows partition and give that to the ubuntu partition.

I have used Gparted and windows disk management before, but I'm not sure how to shrink a partition and the assign this new free space to an existing partition.

thanks.

---

### Post by LowSky on 2008-08-20
Well I would make sure to defragment the hard drive in VIsta b4 you shrink it so you don't loose any files

---

### Post by appi2012 on 2008-08-20
It is not that hard to do in GParted (Ubuntu LiveCD) Just right click on the partition you want, and select the "shrink" option. (Use the vista defragmenter first) That will let you make it smaller. Then just use the "grow" option on your ubuntu partition, and resize it to fill the space.

---

### Post by cybrsaylr on 2008-08-21
Since you have Vista you may want to use the Vista Partitiong tool.
Vista is a big OS and the MS tool will recommend have far you can shrink Vista so as not to damage the Vista partiton.

I also have a dual boot setup with Vista/Ubuntu.
You can get to the Vista shrink tool by I think,

Control pannel>system administration>storage
Then right click on the Vista partition and click on the shrink choice I believe.....(it's been awhile since going in there).

Make sure you defrag Vista first.
Then Vista will tell you how far you can shrink it down.
IMHO I wouldn't go < 40GB.

---

