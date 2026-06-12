---
title: "[SOLVED] no root file system defined 8.10"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by tadcan on 2008-11-01
I had a dual boot system. I now have two partitions of XP sp3 and an area of free space. 

when I use the live cd to install I use the manual option to fill the free space. When I click on proceed I am told 'no root file system defined'. How do I solve this.

I have a second HD which I put 8.10 onto. That has been giving me a grub 18 error. Anyway that drive is supposed to be for XP. Long story, read the below link if relevant.    

[http://ubuntuforums.org/showthread.php?t=963421](http://ubuntuforums.org/showthread.php?t=963421)

---

### Post by billgoldberg on 2008-11-01
> **tadcan said:**
> I had a dual boot system. I now have two partitions of XP sp3 and an area of free space. 

when I use the live cd to install I use the manual option to fill the free space. When I click on proceed I am told 'no root file system defined'. How do I solve this.

I have a second HD which I put 8.10 onto. That has been giving me a grub 18 error. Anyway that drive is supposed to be for XP. Long story, read the below link if relevant.    

[http://ubuntuforums.org/showthread.php?t=963421](http://ubuntuforums.org/showthread.php?t=963421)

You have to set a "/" as a mount point for your root partition.

---

### Post by tadcan on 2008-11-01
Thanks that worked!

On a side not, the first time I tried the install I got an I/O error. It was suggested to me the CD drive or HD could be damaged.... or maybe just maybe I'd left a great big thumb print on the live CD.... :)

---

