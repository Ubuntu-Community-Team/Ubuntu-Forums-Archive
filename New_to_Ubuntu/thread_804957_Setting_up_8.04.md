---
title: "Setting up 8.04?"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by groeswenphil on 2008-05-23
Hi,
I have a duel boot system. I run XP and .....well I used to run Dapper, but after trying to upgrade across the network the system broke.
Now I've got 8.04 on a disk.
I'm pretty sure that I can go ahead and install it....but I'm wondering, should I get rid of the old installation or will the new stuff just over-write?

Thanks,
Phil

---

### Post by SunnyRabbiera on 2008-05-23
a clean install will be fine, but if you want to back anything up I suggest you do it.

---

### Post by neurostu on 2008-05-23
When you run the ubuntu installer it will give you 3 options.
1- Install Ubuntu and use the entire HDD
2- Install Ubuntu over a previous linux install
3- Create a new partition to install ubuntu on.

Which of the 3 you chose is up to you, if you're not going to use windows I would chose option 1.

Note: The options ubuntu gives you might not be spelled out the way I wrote them, but those are basically the options you will be presented with.

---

### Post by groeswenphil on 2008-05-23
2- Install Ubuntu over a previous linux install
This is what I want to do..........but I think the option given was manual install.....I'd choose that one?
Phil

---

### Post by neurostu on 2008-05-23
Yes you want to do a manual configuration. It will bring up a list of your current partitions. Don't touch the SWAP or NTFS partitions. Select the ext3 partition, reformat it to ext3 and set its mount point at '/' then install to that new ext3 partition.  This will leave your windows partition intact.

---

