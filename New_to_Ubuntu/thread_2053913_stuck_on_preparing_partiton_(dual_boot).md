---
title: "stuck on preparing partiton (dual boot)"
date: 2012-09-06
forum: New to Ubuntu
---

### Post by djokja on 2012-09-06
hello, today i'll instal ubuntu 8.04 lts on my laptop. I have read  installation instruction from book, and i try to use dual boot option (i  have install Windows XP on that laptop). 
The problem is i got stuck on preparing partition. Can anybody help me about this?
I just afraid if my hardisk formatted and the whole important data lost  

thanks before :wink:

---

### Post by lukeiamyourfather on 2012-09-06
Before you do anything else get a supported version of Ubuntu, like Ubuntu 12.04 LTS.

---

### Post by oldfred on 2012-09-06
Welcome to the forums.

And if system is older and does not have a lot of memory Xubuntu or Lubuntu may be better but newer distributions.

[https://help.ubuntu.com/12.04/installation-guide/amd64/minimum-hardware-reqts.html](https://help.ubuntu.com/12.04/installation-guide/amd64/minimum-hardware-reqts.html)

Lubuntu, which uses the LXDE desktop environment, targeted at "normal computers" with 128 MB
With 512Mb of RAM and almost any processor, Lubuntu will perform more than adequately out-of-the box. 
I'd suggest to check amjjawad's thread (Lubuntu One Stop Thread) and you'll find many useful information.
[https://help.ubuntu.com/community/LubuntuLinks](https://help.ubuntu.com/community/LubuntuLinks)

What partitions do you have now?

Post this from liveCD terminal:

```
sudo fdisk -lu
```

Basics of partitions:
[http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

