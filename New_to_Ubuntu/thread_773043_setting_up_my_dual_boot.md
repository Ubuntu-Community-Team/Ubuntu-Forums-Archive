---
title: "setting up my dual boot"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by koolh on 2008-04-28
Hi all,

So I'm pretty new to setting up dual boots and stuff, so I was hoping I could get some advice here. :)

I've just put together a new rig, and installed XP on it. I made a 160GB partition on my 500GB disk in the Windows installer, so right now, I've 160GB allocated to XP, and 340GB unallocated.

Ok, so 8.04 is now out, and I'm all set to do a dual boot installation. I've been reading around and especially [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning), and I was just wondering which arrangements would you guys recommend. I've 4GB RAM:

either:
1. 160GB NTFS partition for XP
2. 250GB NTFS partition for Shared Data
3. 50GB ext3 partition for /
4. 10GB ext3 partition for /home
5. 4GB for swap
and use NTFS-3g

or:
1. 160GB NTFS partition for XP
2. 260GB ext3 for /home
3. 40GB ext3 for /
4. 4GB for swap
and use FS-Drive


Thanks in advance, and please feel free to give me advice on the space allocation and such. Thanks!

---

### Post by bodhi.zazen on 2008-04-28
First 4 Gb swap is likely too big. In general the more ram you have the less you need swap. With 4 Gb you are likely to never use is.

The rule of thumb is swap = RAM X 2 , max 1 Gb, or if you have a laptop and use suspend, swap = RAM.

Next, Ubuntu can be installed in as little as 10 Gb. So 20 Gb for Ubuntu would be more then enough.

Use the rest of your hard drive for a shared data partition. You can use NTFS or ext3 for a shared data partition.

Or make additional 10 Gb partitions for tesing other distros or better VMWare / VirtualBox.

---

### Post by damis648 on 2008-04-28
I agree 4 gb is too big unless you suspend, however i am not sure if you know this or not, but you do not need a /home partition. If all you create is a / partition, /home will be in this partition. I have used this configuration for almost two years with various linux distros and it works fine with only a / partition and a swap. I use this because i never know how many applications i am going to install (i install alot). This is what i recommend, however if you want to share data easily with windows and linux, this is what i recommend:

160 gb NTFS: windows
2 gb SWAP
38 gb FAT32: shared
300 gb EXT3: / for ubuntu

---

