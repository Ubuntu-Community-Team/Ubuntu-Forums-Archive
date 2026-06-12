---
title: "Best installation method for my system"
date: 2013-03-06
forum: New to Ubuntu
---

### Post by despidey44 on 2013-03-06
I've already installed 12.10 on my netbook and like it so well that I want to install it to my main desktop and eventually wean off Windows 8. I want a dual boot configuration but had some trouble with doing that when I tried it on my netbook.

Am I best off creating a new partition and then installing to that or does the Ubuntu installer create the partition for me, and if so, how can I control the size?

Dell Studio 540
Win8 64bit
2.33Gig Core2 Quad
4GB RAM
640GB HD w/375 available
ATI Radeon HD 3450 display adapter

---

### Post by slickymaster on 2013-03-06
[Ubuntu installation guide]("https://help.ubuntu.com/community/Installation")

---

### Post by Paqman on 2013-03-06
> **despidey44 said:**
> 
Am I best off creating a new partition and then installing to that or does the Ubuntu installer create the partition for me, and if so, how can I control the size?


The installer can do that for you. I haven't messed about with partitions for ages but IIRC you get a bar that you can drag back and forth to decide how much space to give to each system. Make sure you leave Windows with about 20% or so on top of what it's actually using, or you'll get bad fragmentation on the Windows side. Ubuntu needs a minimum of about 10GB to work well, but more is obviously better.

Ubuntu can access data on an Windows partition, but Windows can't access data on the Ubuntu side. So you might want to have a think about how you'll share data between them.

---

### Post by Cheesemill on 2013-03-06
If you want to use the ATI graphics drivers on that machine instead of the open-source drivers that come with Ubuntu then you can't use 12.10 or 12.04.2 on that machine.

ATI dropped all support for the 2/3/4xxx series of graphics chipsets last summer, meaning there are no proprietary drivers available for these cards for newer versions of Linux.

If you want to have proper support with the ATI drivers then you should use the 12.04.1 release available [here]("http://old-releases.ubuntu.com/releases/12.04.1/").

---

### Post by despidey44 on 2013-03-06
Is there a discernible difference between 12.04.1 and 12.10 that a non-technical guy like me would care about?

---

### Post by Cheesemill on 2013-03-06
12.10 has slightly newer versions of software and supports newer hardware, but is only supported for 18 months.

12.04 is an LTS release which means it gets support for 5 years. Also some people find it to be a more stable than 12.10.

---

