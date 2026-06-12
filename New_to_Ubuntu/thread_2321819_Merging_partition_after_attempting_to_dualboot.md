---
title: "Merging partition after attempting to dualboot"
date: 2016-04-24
forum: New to Ubuntu
---

### Post by dustinlowe17 on 2016-04-24
So the day Ubuntu 16.04 released, I decided to download the iso and put it on a usb drive. I booted it up as normal and attempted to dualboot it with Antergos already installed. As it was installing, the installer suddenly crashed with an error message that said something about my hard drive being too old or hot but I was sure this was not the case as it was working fine. But after I attempted it again by downloading it through the torrent and getting the same error, I decided to just give up. However, now I have a partition that Ubuntu created. So what I want to know is how to merge the partition that Ubuntu created back to my Antergos Root? Attached is a screenshot of my partition disk info.

---

### Post by grahammechanical on 2016-04-24
You run Gparted from a live session. Set the swap partition to swap = off and then resize/shrink the Extended partition (sda3) back to the size of the swap partition. That should create unallocated space behind sda2. Finally resize/expand sda2 to take up the unallocated space.

By the way, the Ubuntu partition was not created. What would have been the Ubuntu partition is shown as 201 GB free space.

Regards.

---

### Post by dustinlowe17 on 2016-04-24
Oh duh. It worked like a charm. Thank you so much :)

---

