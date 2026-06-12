---
title: "Weird Partition Problem"
date: 2007-06-07
forum: Other OS Talk
---

### Post by init1 on 2007-06-07
I was a in Linux Mint live CD session using gparted. I had a partition that I did not need so I deleted it and tried expanding the adjacent partition to fill the space. During the partition resize, gparted gave me some error and there appeared to be a problem because I could not mount the partition after. So I rebooted and ran gparted in Mepis, and although the partition had been expanded, there was excess space that was taken up. I then mounted the partition and did a "du", which told me that the correct amount of information was on the partition. Which should I trust? du, which says what I expected, or df and gparted which says that there is more information on there than I expected? What happened?

---

### Post by kidders on 2007-06-28
Hi there,

Partition resizing is very unsafe (as you've noticed), and should be avoided. Something worth mentioning before going any further is that the amount of space that's "not used", and the amount of space that's "free" are not the same thing. Could that be the source of your confusion?

---

### Post by init1 on 2007-07-02
> **kidders said:**
> Hi there,

Partition resizing is very unsafe (as you've noticed), and should be avoided. Something worth mentioning before going any further is that the amount of space that's "not used", and the amount of space that's "free" are not the same thing. Could that be the source of your confusion?
This is a bit exaggerated, but it shows the situation. 
Before:
===============000000000|======0000000000|
The "=" is the used space, and the "0" is the 
free space and the "|" separates the partitions
After:
==================================000|

Gparted showed a longer used space bar after than before I deleted one partition and resized the other to fill it. I don't know were that extra space came from, but it robbed me of some HD space...
Maybe I will just delete that partition...

---

### Post by kidders on 2007-07-02
Hmm... Time for some details, I think. What filesystem(s) are involved? How big are they? Are they healthy? What kinds of space consumption differences are we talking about? (ie something of the order of megabytes? gigabytes?)

---

### Post by init1 on 2007-07-02
Ext3 in both, I think. Not quite a GB in difference, but more than a few MB. The partition was large, 30GB? 40GB? Something like that. It was old, I had moved it around several times before. It was the remnants of an edgy install. I had lots of ISO's stored in it, so when I deleted system files and it no longer worked well, I removed all but my home folder. Thanks for your help, I didn't think anyone would respond...

---

