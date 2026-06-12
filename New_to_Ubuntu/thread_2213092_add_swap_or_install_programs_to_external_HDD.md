---
title: "add swap or install programs to external HDD"
date: 2014-03-24
forum: New to Ubuntu
---

### Post by Nova_White on 2014-03-24
So i have an old Dell Mini 9 that I decided to pull out of my closet to install Ubuntu onto. The main reason i stopped using my old netbook is because the SSD gave out. So I decided to install Ubuntu onto an 8gb flash drive , It's main purpose is so I can type up google documents on the go without having to carry my primary laptop which is heavier and takes up more bag space. I also use it for midi recording on Rosegarden every once in awhile.
Now, i notice some lag sometimes which is understandable since its running from a usb but i was wondering if its possible to add addition swap space from (or using) an external hdd ? and if so, how?

also how can i install applications onto my HDD that has 64gb of unallocated space ( previously had linux mint 16 on it )
i read something about making a /usr partion but i need a bit more of an explanation 


Thanks :)

ps. im running the latest ubuntu

---

### Post by sandyd on 2014-03-25
> **Nova_White said:**
> So i have an old Dell Mini 9 that I decided to pull out of my closet to install Ubuntu onto. The main reason i stopped using my old netbook is because the SSD gave out. So I decided to install Ubuntu onto an 8gb flash drive , It's main purpose is so I can type up google documents on the go without having to carry my primary laptop which is heavier and takes up more bag space. I also use it for midi recording on Rosegarden every once in awhile.
Now, i notice some lag sometimes which is understandable since its running from a usb but i was wondering if its possible to add addition swap space from (or using) an external hdd ? and if so, how?

also how can i install applications onto my HDD that has 64gb of unallocated space ( previously had linux mint 16 on it )
i read something about making a /usr partion but i need a bit more of an explanation 


Thanks :)

ps. im running the latest ubuntu

Hi, it would be possible, but it would be slower due to the fact that it is accessed via USB.
Basically, you would
a) Use Gparted to create a swap partition on your external HDD
b) run
```

sudo swapon /path/to/partition
```
Where /path/to/partition is your swap partition.

You can find /path/to/partition by running 
```

sudo fdisk -l
```
which will output something similar to ```

root@JewelStaite:/etc/nginx/sites-enabled# fdisk -l

Disk /dev/vda: 32.2 GB, 32212254720 bytes
255 heads, 63 sectors/track, 3916 cylinders, total 62914560 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d2cdd

   Device Boot      Start         End      Blocks   Id  System
/dev/vda1   *        2048    60817407    30407680   83  Linux
/dev/vda2        60819454    62912511     1046529    5  Extended
**/dev/vda5        60819456    62912511     1046528   82  Linux swap / Solaris**

```
In this case, I would replace /path/to/partition with /dev/vda5.

You can do this automatically by finding the UUID of the partition, and adding it along with mount options to /etc/fstab.

What I would reccomend is instead mounting the external HDD inside the netbook if possible. That will allow you to have faster performance while having a simpler configuration.

Please post back if you need more help :)

---

