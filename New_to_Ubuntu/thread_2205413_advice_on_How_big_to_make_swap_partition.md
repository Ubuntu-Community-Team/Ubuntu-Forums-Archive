---
title: "advice on How big to make swap partition"
date: 2014-02-13
forum: New to Ubuntu
---

### Post by LinuxVirgin2000 on 2014-02-13
Hi, Just wanting some advice on how big I should make my swap partition for 12.04 LTS

My ultra book has 8gb of RAM, but since i'm going to be dual booting there will only be around 40-50gb of SSD space left for ubuntu so just wondering how big does the swap actually need to be?
I mostly use my ultrabook for internet, word processing/PDF editing, music/videos, and very rarely I edit very big image files in G.I.M.P but not very often.

thanks

---

### Post by radwanski-michal-a on 2014-02-13
I won't even create swap partition. Every write process on SSD damages it. With that amount of RAM, I would install OS without swap.

---

### Post by Impavidus on 2014-02-13
It depends on whether you want to hibernate. If so, make swap slightly larger than your ram. If not, you don't really need it. You could make a little swap partition to get a warning (by the slow-down) when you're running out of memory, so you can quickly close a big program before things start crashing. Instead, you can use a memory monitor too. Even if you have swap, your system will hardly ever use it, so it won't destroy your SSD at once.

---

### Post by fantab on 2014-02-14
If you also have a HDD then you can make a SWAP partition on it. Though with bigger RAM SWAP is not really needed but it is a good idea to have one.
Read: [URL="https://help.ubuntu.com/community/SwapFaq"]https://help.ubuntu.com/community/SwapFaq
[/URL][https://help.ubuntu.com/community/Partitioning/Swap](https://help.ubuntu.com/community/Partitioning/Swap)

What Impavidus says about 'Hibernation' is spot on. Your SWAP size should be equal to greater tha your RAM in GiB, not GB. However there are reported issues with 'hibernation' in Ubuntu and I won't recommend it, for now.

I have a 4GiB RAM and I have 4GiB SWAP. I don't use 'Hibernate'.

---

### Post by Bucky Ball on 2014-02-14
2Gb. If you hibernate, make it the size of your installed RAM. Keep the /swap on a HDD if you have one space on one and one plugged in.

/swap is really the least of your worries, as mentioned, it probably won't get touched often. What you should be thinking about is setting up trim for the SSD. That is essential. 14.04 will include a weekly cron job for trim, but right now you need to set it up manually. 

Lots of information about this online. Search for 'trim ssd ubuntu 12.04' and start digging. A cron job is preferable to using 'discard' in the fstab (although 'noatime' should be used in the fstab for all partitions on the SSD). ;)

You can go crazy and keep /opt, /var, /usr, and even /home on another drive, but how far do you want to go? If you move too much stuff it kinda defeats the purpose of having an SSD! One feasible option is to run /tmp in RAM. There's lots of info on how to do that out there, too.

---

### Post by Psil0cybin on 2014-02-15
I do not know about an SSD, but from what I learned you always make a swap the same size of the ram you have, unless you really care about hard drive space,  than a swap is **not** needed.

---

### Post by buzzingrobot on 2014-02-15
Swap is intended to be space on the hard drive that compensates for temporary lack of RAM.  Keeping things simple, if you load enough programs, drivers, etc., that they exceed the available free RAM, the OS writes some part of the data in RAM out to the swap partition on disk.  These data are accessed when needed, transparently, by programs, but, of course, reading and writing to a hard drive is much slower than reading and writing to RAM.  

Hibernation involves writing all of RAM, in use or not, to the swap partition.  When the machine is restarted, all that data is reloaded to create the impression that you have picked up where you left off.  To make this work, the swap partition needs to be at least the same size as RAM in the machine.

If you think you will, sooner or later, need to hibernate, then create a swap file equivalent in size to you RAM.

Otherwise, the size of the swap partition really depends on how many applications you will load simultaneously.  For 8 gigs of RAM, and typical usage, I'd create a 1 or 2 gig swap file.  If that is not enough, you can always enlarge it later.

(You can load the apps you usually run and use System Monitor to determine how much RAM is in use.)

---

