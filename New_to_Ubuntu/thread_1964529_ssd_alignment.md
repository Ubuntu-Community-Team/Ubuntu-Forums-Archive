---
title: "ssd alignment"
date: 2012-04-24
forum: New to Ubuntu
---

### Post by StevenSeagull on 2012-04-24
Thanks a lot very interesting thread. I installed 12.04 after a few tries and everything is working fine, but I'm wondering about one thing that is pretty obscure to me, ssd alignement, how do you check, did gparted take care of that, should I worry about it?

Here's what I get with gdisk :

> 
gntz@gntz-ThinkPad-X220:~$  sudo gdisk /dev/sda
[sudo] password for gntz: 
GPT fdisk (gdisk) version 0.8.1

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.

Command (? for help): p
Disk /dev/sda: 234441648 sectors, 111.8 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 95F5725B-A364-4B03-9E91-9C5C05B6F6E4
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 234441614
Partitions will be aligned on 1-sector boundaries
Total free space is 2539 sectors (1.2 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048           77823   37.0 MiB    EF00  
   2           78333       234441598   111.8 GiB   0700  



---

### Post by mörgæs on 2012-04-24
Moved to a new thread as this is a new subject.

---

### Post by SlugSlug on 2012-04-24
I've benchmarked a few ssd's with and without alignment.

In my case it only made a couple of MB/s difference.

I followed this guide
[http://lifehacker.com/5837769/make-sure-your-partitions-are-correctly-aligned-for-optimal-solid-state-drive-performance](http://lifehacker.com/5837769/make-sure-your-partitions-are-correctly-aligned-for-optimal-solid-state-drive-performance)

you can check with 

sudo hdparm -t /dev/sda

my results on a live server..

Timing buffered disk reads: 694 MB in  3.00 seconds = 231.26 MB/sec

---

### Post by StevenSeagull on 2012-04-24
> **SlugSlug said:**
> I've benchmarked a few ssd's with and without alignment.

In my case it only made a couple of MB/s difference.

I followed this guide
[http://lifehacker.com/5837769/make-sure-your-partitions-are-correctly-aligned-for-optimal-solid-state-drive-performance](http://lifehacker.com/5837769/make-sure-your-partitions-are-correctly-aligned-for-optimal-solid-state-drive-performance)

you can check with 

sudo hdparm -t /dev/sda

my results on a live server..

Timing buffered disk reads: 694 MB in  3.00 seconds = 231.26 MB/sec

Thanks a lot, I am going to try that.

---

### Post by Grenage on 2012-04-24
I'm slightly surprised it makes much difference on an SSD; I aligned mine when installing, but I suspected it wasn't required.  I might change the alignment and see how it changes.

---

### Post by SlugSlug on 2012-04-24
> **Grenage said:**
> I'm slightly surprised it makes much difference on an SSD; I aligned mine when installing, but I suspected it wasn't required.  I might change the alignment and see how it changes.


It wasn't much difference - only a few MB/s but for the sake of a 15min job... why not :)

---

### Post by audiomick on 2012-04-24
Does the alignment make any difference to speed or anything other than just the available space?

---

### Post by SlugSlug on 2012-04-24
it added a small speed increase ( a couple of MB/s ) making sure ACHI is enabled in the BIOS makes more of a difference

---

### Post by audiomick on 2012-04-24
Thanks, I'll check that. I have an SSD in my desktop for / , but I just stuck it in and installed on to it. Works fine, but more speed is always good...

---

### Post by SlugSlug on 2012-04-24
mine went from about 190MB/s to 230MB/s turning AHCI on.

unfortunately you can't do that on windows it blue screes if you swap :D

---

### Post by StevenSeagull on 2012-04-24
Success. It aligned my root partition, now both partitions are aligned. Took a while and I don't notice any difference but it makes me feel better lol, thanks again Slugslug. Forgot to run the speed test before tho :mad:.

---

### Post by audiomick on 2012-04-24
> **SlugSlug said:**
> mine went from about 190MB/s to 230MB/s turning AHCI on.

unfortunately you can't do that on windows it blue screes if you swap :D

Good thing there's no Windows on my desktop, then, eh? :p

---

### Post by Grenage on 2012-04-24
> **SlugSlug said:**
> mine went from about 190MB/s to 230MB/s turning AHCI on.

unfortunately you can't do that on windows it blue screes if you swap :D

For the record (not that it will affect many of us), you can get around that by making a registry alteration before making the change. :)

---

### Post by mörgæs on 2012-04-24
> **StevenSeagull said:**
> Success. It aligned my root partition, now both partitions are aligned. Took a while and I don't notice any difference but it makes me feel better lol, thanks again Slugslug. Forgot to run the speed test before tho :mad:.

Good, then please mark the thread 'solved'.

---

### Post by SlugSlug on 2012-04-24
> **Grenage said:**
> For the record (not that it will affect many of us), you can get around that by making a registry alteration before making the change. :)


Ahh good to know thanks, am upgrading customers old PC's with ssd's

---

