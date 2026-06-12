---
title: "Swap size?"
date: 2013-01-15
forum: New to Ubuntu
---

### Post by Yezinki on 2013-01-15
My machine running Ubuntu has /30 GiB ext4, /home 263 GiB ext4 & swap 5 GiB.

It has 2 GB of RAM memory.

Should the swap size be 4 instead of 5 GiB?

Would reducing it to 4 make any difference?

If yes can it be done using GParted Live CD, where would I transfer the 1 GiB?

I have none issues with 5 GiB of swap.

Thanks.

---

### Post by squakie on 2013-01-15
With that much disk space already available to ubuntu, I wouldn't worry about your swap size - it's probably not worth the hassle just to get 1 to 3 gig back.

---

### Post by NikTh on 2013-01-15
Hi , 
read the swapfaq here : [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
It will solve lot of queries. 

Thanks

---

### Post by Yezinki on 2013-01-16
Thanks NikTh for your reply & the posted link.

1. Although my Ubuntu setup has a swap size of 5 GiB, but is rarely used. The sytem uses physical memoray till about 800 MiB.

2. The only time I see a few kb of swap being used is when I have Pidgin, Skype, 4/5 tabs of G Chrome open & am watching a movie using VLC, it is that time that 50-80 kb of swap being used.

3. Hypothetically if I feel to decrease it can I do it on a Live running system using GParted Live CD, if yes where would that 1 GiB of swap go. As posted earlier root is /30 GiB ext4, /home 263 GiB, to home?

---

### Post by Elfy on 2013-01-16
I'd add it to /home - but to be honest I wouldn't bother at all for 1Gb ;)

---

### Post by Yezinki on 2013-01-16
Thanks Elfy for sharing your expert thoughts.

Btw how can it be added to /home?

---

### Post by Elfy on 2013-01-16
Without knowing the exact layout it's hard to tell.

Assuming that swap is after /home you'd shrink swap and then expand /home. If swap is inside an extended on it's own - you'd need to shrink both swap and the extended before you can add it to /home/

```
sudo fdisk -l
``` will give more information

Make sure you have backups just in case the partitioning goes wrong ;)

Edit - I still think it's a lot of work for 1Gb :lol:

---

### Post by Yezinki on 2013-01-16
```
vaio@VGC-LS1:~$ sudo fdisk -l
[sudo] password for vaio: 

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x34734b0d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    62916607    31457280   83  Linux
/dev/sda2        62916608   614467583   275775488   83  Linux
/dev/sda3       614467584   625141759     5337088   82  Linux swap / Solaris
vaio@VGC-LS1:~$ 
```

Exactly swap is after home.

---

### Post by Yezinki on 2013-01-16
Agreed totally is alot of work for 1 GB........:D

1 last question about it can one do it using GParted?

Thanks.

---

### Post by squakie on 2013-01-16
> **Elfy said:**
> I'd add it to /home - but to be honest I wouldn't bother at all for 1Gb ;)  That's exactly what I thought - I think I put that in my post and I'm glad someone agreed with me that with all the disk space the OP has already allocated to linux, it's a lot of work with such a small return. ;)

---

### Post by Elfy on 2013-01-16
> **Yezinki said:**
> Agreed totally is alot of work for 1 GB........:D

1 last question about it can one do it using GParted?

Thanks.

Yep - you'll need to do it from a live environment though as you need /home to be unmounted, you'll also probably need to turn the swapoff. 

Then you'll be able to resize swap and then expand /home.

---

### Post by audiomick on 2013-01-16
Another vote for leaving it alone. My desktop has 15GB for 8GB RAM. I've got more drive space than I can poke a stick at, so I set it big. I does not cause me any problems at all. I might reduce it at the next clean install, but then again I might not.

If you are not really tight for drive space, leave it alone. Messing around with your partitions always carries a slight risk. Also, if 1 or 2 GB of drive space is that critical, you should be thinking about a bigger or an additional drive.

---

