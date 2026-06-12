---
title: "move /home to a new partition"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by Lowcountry on 2008-06-11
I had some unallocated space on my harddrive, so I decided to grow my /home partition.  During the process, my computer locked up and now I can't boot Ubuntu anymore.
I really don't want to loose the data on that partition.  I do have an unused formatted partition on my hard drive.
How can I move all of that info. to the new partition and then use it as home?
Or what should I do?
Thanks

---

### Post by drs305 on 2008-06-11
It may depend on what happened during the copying.

Can you boot the ubuntu livecd? If so, you should be able to mount the partition on which you have data and see if it was compromised. If not you can transfer it to another medium. You will need to know the name of the partition with the data on it so you can mount it. 

If you need instructions check back here.

---

### Post by Lowcountry on 2008-06-11
> **drs305 said:**
> It may depend on what happened during the copying.

Can you boot the ubuntu livecd? If so, you should be able to mount the partition on which you have data and see if it was compromised. If not you can transfer it to another medium. You will need to know the name of the partition with the data on it so you can mount it. 

If you need instructions check back here.

Yes, I can boot the livecd.  Where do I go to mount it?

---

### Post by ukripper on 2008-06-11
Check this link : [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

it worked for me.

---

### Post by drs305 on 2008-06-11
> **Lowcountry said:**
> Yes, I can boot the livecd.  Where do I go to mount it?

First,  you have to open a terminal. Accessories, Terminal. 

Then run **fdisk -l ** to get a list of your partitions.

If you recognize the partition with your data on it, make a note of it. If you didn't have a separate partition for your data, it should be part of your original root directory ( / )

Make a mount point:
```
sudo mkdir /temp
```

Mount the original root partition (or the one with your data) onto /temp:
```
sudo mount /dev/**sda1** /temp
``` 

Open nautilus and look at /temp to see if you can find your files.


If your files look okay, try to copy them to a CD, flash drive, etc. 


Makeing sure you didn't lose you files was the first priority, Maybe we can restore your original ubuntu installation. What happened when you tried to boot to ubuntu?

---

