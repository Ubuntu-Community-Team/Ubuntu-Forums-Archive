---
title: "Need help. Not enough disk space"
date: 2017-02-23
forum: New to Ubuntu
---

### Post by trollex2 on 2017-02-23
Hi, I'm new to ubuntu and I've not really installed anything other than steam. I run ubuntu alongside W10 and I wanted to try linux out. However, when I try to download/install CSGO, I get an error saying that I only have around 1000mb left, when I put aside 100GB from W10. When I went to gparted, it said that I was not using the 100GB unallocated space. I looked it up online and I found a post saying I should open gparted and resize ubuntu into the partition. I tried doing that but the unallocated space is in /dev/sda and my ubuntu is in /dev/sdb.
I'm new so I'm sorry for wasting any time for a most likely simple solution. Please help me out.

---

### Post by SeijiSensei on 2017-02-23
One solution is to format the unallocated space and assign it to /home.  See [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving).  Whether that helps enough depends on how much stuff you've stored in the home directories.  It's the easiest solution, one that doesn't require reinstalling the operating system.

---

