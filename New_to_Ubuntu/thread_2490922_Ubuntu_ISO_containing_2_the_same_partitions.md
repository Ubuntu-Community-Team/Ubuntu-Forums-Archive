---
title: "Ubuntu ISO containing 2 the same partitions ?"
date: 2023-09-20
forum: New to Ubuntu
---

### Post by mintingterabyte on 2023-09-20
Hi,

I have noticed some weird behaviour with Ubuntu ISO that I downloaded and wanted to double check if it's by design or there's something weird going on with my ISO. Using Ubuntu 18.04, I have downloaded Ubuntu 22.04 ISO from the official Ubuntu website as well as checked the checksum of the image and it all matches up. I then proceeded to burn the said ISO file using dd command onto my SanDisk Cruzer Blade USB. I'm not sure why but once dd completed the session, 2 the same partitions with the same names have popped up in the file explorer which confuses me. Both are named something like Ubuntu 22.04 LTS x64.

When I clicked on the first partition, it throws up an error with a partition that doesn't even exist on my USB, for example lets say my USB is \dev\sdb with partitions sdb1 and sdb2, the said partition was referencing sdb3 that didn't existed therefore resulting in an error. When I clicked on the second partition, it opened all the files that were burned onto my USB. I noticed that after burning Ubuntu 22.04 ISO, it's all in ISO 9660 format with only one partition being visible in GPARTED but when I check it in the Ubuntu 18.04 file explorer it somehow lists 2 of them, does ISO 9660 format contain more partitions within itself or am I missing something ? I'm confused at the moment as I'm trying to determine if my ISO file is somehow dodgy or not. 

I'm also surprised that there are 2 Ubuntu 22.04 partitions placed onto a USB\ISO file as previous versions of Ubuntu only had 1 when you checked the file explorer known as Nautilus in Ubuntu.

Help is much appreciated.

---

### Post by VMC on 2023-09-20
What's the exact dd command you used? Something in this order:
```
sudo dd if=<the ISO> of=/dev/sd? bs=8M
```

---

