---
title: "How to interpret df command"
date: 2019-01-14
forum: New to Ubuntu
---

### Post by redus on 2019-01-14
So when I put in df or df -h I get a bunch of information, but I'm not sure how useful any of it is. I feel like I should see something like 256 Gb as the total (really I think it's 225 Gb or so) and then of course I'd be using some amount of that. I see about a dozen lines or so, half with a usage not 100%, and none of the totals are near 225 Gb. What exactly am I looking for so I can see how much space I'm using on my solid state drive? Is there an easier way to view how much space I'm using in my ssd (perhaps something outside of the terminal)? Thanks all!

---

### Post by The Cog on 2019-01-14
Without seeing your df -h output it's difficult to know what to say. But you are probably only interested in the lnes that start with /dev/sd, probably /dev/sda as these lines will correspond to partitions on the disk.

---

### Post by redus on 2019-01-14
OK I found an easier way to view the disk usage. If you click on the Show Applications dots >> Utilities >> Disk Usage Analyzer. Boom!

---

