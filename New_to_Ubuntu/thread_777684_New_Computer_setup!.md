---
title: "New Computer setup!"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by k1ngb0b0 on 2008-05-01
Alright, I ordered a new computer and I'm finally taking the plunge into Ubuntu :)  There's a couple things I'm not sure about though...

First, I'd like to do a manual partition so I can keep my data protected if something bad happens.

I have a 250g hard drive.  This is what I was thinking about doing..

10gb primary partition for /
extended partition that uses all the remaining space
2gb swap inside extended (though, I have 4g of ram, should I increase this to 4?)
the rest of the free space in the extended partition for /home

Would that above setup be a good way to go about doing it?  I'm only going to have 1 OS and 1 user for my machine. 



Also, I'm not sure what Ubuntu to get between 32 bit and 64 bit.  I've read a bunch of articles about it but I'm still having trouble deciding...


Any input would be greatly appreciated! :-D

---

### Post by phr0ze on 2008-05-01
I don't know what you plan to install but I'd give a little more to / Also for the swap, I'd let ubuntu pick. Use the rest for your home.

I prefer 32bit for the most compatability. I've never seen any proof of a speed increase or other gains from 64bit except in very special situations, but I see tons of people fighting with particular software or hardware because of it.

---

### Post by bobpur on 2008-05-01
You didn't show the specs for your machine but if it is a dualcore or better you can use a 64 bit OS if you want to. 32 bit OS's can be used in anything that has enough power to run them.
As for benefits of 64 bit, some audiophiles tell me that it gives better sound than 32 bit. I couldn't see it myself. :) Also, slightly faster performance. 
64 bit OS's have improved over the last couple of years and aren't as "buggy" as they used to be. I've run a couple recently and they've done fine. 
I do think 32 bit OS's still have a slight edge in stability, though.

---

### Post by herbster on 2008-05-01
Did you buy a 64-bit processor?

That partition setup is fine. You don't need more swap, though feel free to make it 4gb if you'd like. To keep it simple, swap is only used when your RAM is all used up. I have 4gb ram and a 4gb swap, and running more stuff than I can possibly think of has never taken me past 70% ram usage at most.

---

### Post by bobpur on 2008-05-01
I'd think that with 4 gigs of RAM that a SWAP partition wouldn't be necessary. However, the distro is happier if a SWAP partition is present, I believe.

---

### Post by thisiam on 2008-05-01
i have 1GB swap and 1gb RAM and swap never gets used but if you can spare 4GB you should go ahead. About the 32 bit or 64 bit, you should make sure you have a 64bit CPU if you want to use 64bit Ubuntu and to be able to detect all 4GB of RAM.
32bit detects i think 3.2 GB.

---

### Post by phoenix_abhi on 2008-05-01
For a 4 GB RAM  swap is not necessary. But you got a lot of HD space allotting the swap is Ok. But still it is useless in Ubuntu. 32 or 64. A sea of discussions are available to read. But Technically 8 is superseded by 16 to 32 and future is 64. The graphics and sound are better in 64. If ur processor supports (and today's pcs are definitely) 64 I suggest u go for 64 bit and experience the difference

---

### Post by cubeist on 2008-05-01
Yikes! not another 32 versus 64 thread. Anyway, I have been using 64bit linux for quite some time with no problems whatsoever... but no real difference in speed either... These days the differences between 32 and 64 are minimal.  Once in a while you may find an obscure piece of software that has not been compiled for 64.  In these cases you can generally compile from source... which isn't that hard!

---

### Post by bobpur on 2008-05-01
Performance is, probably, close enough so that a well maintained 32-bit machine with quality parts (A couple of Raptors in RAID 0) would eat up a 64-bit machine.

---

