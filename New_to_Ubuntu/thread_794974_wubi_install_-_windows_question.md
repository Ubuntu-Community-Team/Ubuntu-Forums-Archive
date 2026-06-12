---
title: "wubi install - windows question"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by ubunu on 2008-05-15
I'm sure someone has asked this before but I couldn't find it. I'm running on a 'within' install here and having not used my XP OS for a full day I checked the event logs and there were no entries?

I had assumed that running 'within' windows would still require some windows services to run however there were no entries at all?

There aren't any security issues on this box but I am curious, does anyone know of a thread/site that covers this in any detail?

thanks

PS. Apart from a slight performance and potential hard re-boot issues I can't really see any disadvantages to running in this way (wubi) and I think this will prove to be a major winner for getting 'non techie' users to try out. IMHO

---

### Post by Paqman on 2008-05-15
> **ubunu said:**
> 
I had assumed that running 'within' windows would still require some windows services to run however there were no entries at all?


No part of Windows is running when you're in Ubuntu. What Wubi does is create a virtual partition on your Windows drive, then it installs Ubuntu into it. What you're running is 100% Ubuntu.

---

### Post by ubunu on 2008-05-15
Many thanks for confirming that, A far better scenario than I had envisaged. Just to follow up should there be any issues regarding drivers when installing to a separate partition rather than 'within'?

I vaguely remember seeing somewhere that a 'within' install references the existing windows drivers?

I'm prepping another box for a partition install and just wanted to know what I might expect

Thanks again

---

