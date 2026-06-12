---
title: "Formatting Question"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by TriSwords on 2008-09-24
I have installed ubuntu a few times on my laptop for different reason.

When I dedicate the entire drive to it I usually partition it

/boot ~100MB
/     ~20GB
/swap RAM Size + 100 MB (3.1GB since I have 3 Gigs of ram)
/home Remaining ~200GB

I found a tutorial with that above a while back and it is what I more or less use.

However my question is if that is a good way to partition (the /home seems nice if I have to reinstall).

And how big should a swap space really be? I have read 512MB, 1024MB, Size of Ram, and Size of Ram + 100 MB (to allow it to hibernate). 

My laptop hibernates/suspends (not sure what setting I have it set to) when I close it quite a bit, but Im not sure if swap space size really matter for that.

Most articles I find seem to vary in size of swap space. And I was just wondering what people think is the best way to partition?

Thanks
TS

---

### Post by bruce89 on 2008-09-24
A few comments:

[LIST]
[*]/boot partitions are depreciated (I think).
[*]/ needn't be as large. Mine are 10GB.
[*]/swap is usually RAM + a wee bit. 100MB is probably too much extra.
[/LIST]

---

### Post by thefoolnz on 2008-09-24
hello,

i tend to use the following as a standard practice:

first partition is a fixed 256mb boot/recovery partition
 inside this partition i have the grub boot loader files
 and any other tools in folders that maybe need to help repair the system, this isolates the system from that which boots it and also works with the largest number of drives/mobo/bios.

next i have my swap partition which is normally double physical memory or 4gb which every is closer, the double memory thing maybe over kill but older systems require paging memory to work well which the swap file provides. the swap partition is also put under the first 8gb which should help it work with more wider range of machines, here the boot partition should have managed to get the OS up and going and now the page file is gooing

next i do / this i tend to just have taking up the rest of the avaliable space, as harddrive these days are cheap

and if i need more space i simply install a bigger drive and mount it under the rootfs at some meaningful location
transfering existing information onto it if required.

hope this helps

---

### Post by virtuallinux on 2008-09-24
In my experience, newer hardware doesn't use swap much by default.  I've to 2GB of ram and 1GB of swap, but right now I'm running in about 350MB of RAM plus another 700MB in use as cache.  Older hardware or systems with less memory tend to need swap more.  I am pretty sure, however, that in order to hibernate, you need at least as much swap as you have RAM.

---

### Post by bruce89 on 2008-09-24
> **virtuallinux said:**
> In my experience, newer hardware doesn't use swap much by default.  I've to 2GB of ram and 1GB of swap, but right now I'm running in about 350MB of RAM plus another 700MB in use as cache.  Older hardware or systems with less memory tend to need swap more.  I am pretty sure, however, that in order to hibernate, you need at least as much swap as you have RAM.

Yes, the RAM is dumped to swap in this scenario.

---

