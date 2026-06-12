---
title: "scan disk ssd"
date: 2012-12-09
forum: New to Ubuntu
---

### Post by ryandcalvert on 2012-12-09
i recently installed ubuntu 12.04 onto a scandisk extreme 120g, ever sense I have been having freezing issues. I have read several threads on ssd but found nothing dealing with complete freezes. I have to shut down the computer for about 30sec then I can reboot it. Can someone help me understand what I may have done wrong or maybe what I haven't done yet? 
Do I need to activate TRIM? I really don't know what this is but have read about it on a few threads. Would not having it on cause this? Do i have a bad drive? Is there something out there that would test my drive?
thanks:)

---

### Post by Pjotr123 on 2012-12-09
Here's a complete how-to for Ubuntu on an SSD:
[https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd)

Good luck! :)

---

### Post by 3rdalbum on 2012-12-09
Unexplained freezes are usually the result of bad RAM. The best way to find out is to take out all but one stick of RAM, and if everything is okay try the next stick, etc. Replace any sticks that cause your problems.

It is also possible to have no symptoms on Windows but crashes on Linux, due to the way Windows leaves up to 2GiB of RAM unused at all times.

---

### Post by ryandcalvert on 2012-12-09
> Unexplained freezes are usually the result of bad RAM. The best way to  find out is to take out all but one stick of RAM, and if everything is  okay try the next stick, etc. Replace any sticks that cause your  problemsI switched my ram back to my original ram and the problem persisted. I then downloaded memtest 386 4.2 from [COLOR=Red][http://www.memtest.org/](http://www.memtest.org/) [/COLOR]and ran it on my pc. My old ram passed which led me to try and new ram again. It also passed. The only other change I have made to my computer was putting in the SSD. 
> 
Here's a complete how-to for Ubuntu on an SSD:
[https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd)I've now done everything on the list execpt for having 10% unallocated, should I mess with my partition size and get myself a 10% block? This SSD isn't old technology so I wasn't sure how important that part was.

Thanks for all the help, I will run this for the next couple days and keep track of freezes, if any, and report back. :)

---

### Post by Pjotr123 on 2012-12-10
> **ryandcalvert said:**
> I've now done everything on the list execpt for having 10% unallocated, should I mess with my partition size and get myself a 10% block? This SSD isn't old technology so I wasn't sure how important that part was.

Not very important, but executing a manual TRIM command on the EXT4 partitions is probably a good idea.

And check the website of the SSD manufacturer, whether there's updated firmware available for your SSD.

---

### Post by ryandcalvert on 2012-12-13
As long as I don't log in under cinnamon 2D this thing runs great no more freezing, thanks

---

