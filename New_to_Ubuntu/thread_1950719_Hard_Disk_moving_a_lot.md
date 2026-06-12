---
title: "Hard Disk moving a lot"
date: 2012-04-01
forum: New to Ubuntu
---

### Post by Drowz0r on 2012-04-01
Hello all

I'm on Ubuntu 11.10 with a pretty middle/high end machine.

I've found that my hard disk seems to move a lot. This is a lot more noticeable when I'm doing a lot of things at once. On windows I'd expect this to be fragmentation and after a defrag it would stop... though I understand Linux cannot become fragmented, so what is causing it? o.o

My file system is EXT4 if that helps?

Thanks all

---

### Post by zombifier25 on 2012-04-01
It means your hard drive has a lot of stuffs being read/written to it. However, the cause is rather generic (there may be no problem at all)

---

### Post by 2F4U on 2012-04-01
When you say it seems to happen more often when you do a lot of things in parallel it could be a swapping issue. How much RAM do you have in the machine? Do you notice a slowdown?

---

### Post by Drowz0r on 2012-04-05
Hello there

Thanks for the replies. Here is my spec:

OS: Ubuntu 11.10
RAM 3GiB
CPU Intel Quad Q6600 2.40GHz
512 MB RAM GeForce 8800 GT Nvidia

Doesn't appear to be a swapping thing :/

It seems to happen when doing a lot of stuff at once, being looking at multiple web pages or watching youtube videos or something. Not actually burning CDs or something.

When I did the same thing on Windows XP, the disk didn't move nearly as much.

---

### Post by QIII on 2012-04-05
Disks can (and do) become fragmented, despite the myth.  Just not on the rampant wholesale level.

Is your disk moving more or making more *noise*?

---

### Post by Drowz0r on 2012-04-05
> **QIII said:**
> Disks can (and do) become fragmented, despite the myth.  Just not on the rampant wholesale level.

Is your disk moving more or making more *noise*?

The level of the sound is the same as before, it's just more frequent. Comparable to an XP machine if I'd not defraged it for a year or something.

---

### Post by QIII on 2012-04-05
Could you install lm-sensors, run sensors-detect and then install a tool like gkrellm to actually look at disk activity objectively?

---

### Post by Drowz0r on 2012-04-05
> **QIII said:**
> Could you install lm-sensors, run sensors-detect and then install a tool like gkrellm to actually look at disk activity objectively?

I'll take a look around the software centre and stuff for it and let you know how I get on. Thanks! :D

---

