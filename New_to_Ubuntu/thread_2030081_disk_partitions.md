---
title: "disk partitions"
date: 2012-07-20
forum: New to Ubuntu
---

### Post by Paneless on 2012-07-20
Hello, I have just re-installed 12.04 and this time "manually" set my disk partitions. I have attached a screen shot from Gparted as I thought I had allocated 15 Gb for boot but in fact its only 5. Everything seems to be working (for the time being at least) and was just seeking confirmation that this config is ok or whether I will have to do it over again. Thanks, Ryan

---

### Post by OM55 on 2012-07-20
Hello Ryan,

Everything looks good and can work well, excluding the follwing:

1. I noticed however that you left 23GB of unallocated space on the drive. If there is no special reason to do that, I would have added it to the main partition (the large one). But in order to do that you need to remove the Swap partition first (you can consider moving it with GParted, but the time it will take it to move the partition is probably just as much as it will take you to reinstall Ubuntu 12.04...

2. I also noticed that your first partitions are formatted Ext2 and not Ext4. I assume you did that with GParted (which offeres Ext2 by default). Ext4 is superior to Ext2. Why wont you let the Ubuntu installer do the job for you? If you remove all partitions (using GParted) and then install Ubuntu and let it do the partitions automatically - it will do it faster and optimized the best way.

---

### Post by Paneless on 2012-07-20
Thanks for your reply and just to confirm that I have installed again using the default settings. Ryan

---

