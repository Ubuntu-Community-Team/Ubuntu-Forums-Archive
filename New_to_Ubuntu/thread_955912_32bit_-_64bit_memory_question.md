---
title: "32bit - 64bit memory question"
date: 2008-10-22
forum: New to Ubuntu
---

### Post by ITdrummer on 2008-10-22
Hey guys,

I am currently dual booting XP(32-bit) and Ubuntu 8.04(64-bit),  each on a separate hard drive.

My system has 2x1GB 800MHz ram.  I realize that the maximum amount of memory for 32-bit OSs is around 3 gigs.  If I were to double my system memory (2x1GB --> 2x2GB or 4x1GB) would this cause a problem for my Windows OS?  

Im aware that the 64-bit ubuntu would be able to utilize all 4 gigs of RAM.

I guess the real question would be,  Would windows just ignore the extra 1GB of RAM?, or is it not a good idea to run a 32-bit OS with more memory than it can utilize?

---

### Post by Pconfig on 2008-10-22
Windows would just ignore it. Shouldn't give any problems. Ubuntu 64 will be able to address all your memory or course.

---

### Post by AFarris01 on 2008-10-22
Basically, yes, it would be ok to double your RAM, and windows wouldnt really care.

technically the max ammount of RAM a 32-bit OS can utilize is closer to 3.5 gigs.  if you put 4 gigs of RAM in the PC, the windows will utilize something like 3.4GB, and ignore the rest... and ubuntu will use something like 3.8-3.9 GB.

hope that answers your question!

---

### Post by phidia on 2008-10-22
Actually 32 bit linux can "see" more than 4GB of ram if you install the server kernel.

I use 64 bit and support it but this question has come up before and it turns out that 32 bit can use all of the 4 GB (with the server kernel).

Do a search :)

---

### Post by Pconfig on 2008-10-22
Indeed, that's new to me. It seems to be significantly slower though.

[http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)

A nice recourse about PAE (the technique used). Getting a little offtopic though

---

### Post by ITdrummer on 2008-10-22
Thanks everyone.  Thats all I needed to know.

---

