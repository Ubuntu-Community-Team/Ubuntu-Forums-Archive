---
title: "Install  on specific partition"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by thefreddy on 2008-07-11
Hi Guys,
I have wiped out Vista from my dual boot (XP / Vista) system leaving me with spare partition D which I want to install ubuntu 8.04.1.
How do I make sure it installs on D drive?
Partition options on install seem to offer Auto or manual install.:confused:
By the way D is 40gb

Many thanks for any help

---

### Post by Elfy on 2008-07-11
If you use the manual option you can choose which partition to install to - you will also need to edit the partition in order to give it amountpoint of /

You will also need to set it up to format the partition to ext3 

It will make sense once you're in there hopefully :)

---

### Post by thefreddy on 2008-07-11
Thanks forestpixie,
Ok amoutpoint of / (is that complete the /?
will the D drive need sub dividing and into ? sizes.

Regards

---

### Post by Elfy on 2008-07-11
You could if you so wished make a /home parttion - if you reinstall later it can make it easier.

You will need a swap partition as well - 1.5xRAM is default 0 but it depends on available RAM and need to hibernate.

TBH I prefer to use the partition editor (Sys> Admin menu) to get partition sorted before I do the manual option.

I use a / of 9Gb and have 4Gb free
I have swap of 1Gb with 1.3Gb of RAM and on really need it with virtual machines

My /home is 9Gb - I have 7Gb free now that my media re on their own seperate partitions so is probably much too big :)

Food for thought - it does depend on how much you have available and swap needs

Post again for clarification if you need

---

