---
title: "Installing Python in /dev/shm"
date: 2013-01-22
forum: Programming Talk
---

### Post by troymius on 2013-01-22
I have a program that needs to call python often. Now since python needs to be pulled from the hard-drive every time it's called, it slows things down, especially when the HDD is busy serving somebody else at the moment.

So I thought what if I install Python into a ramdisk (/dev/shm) and call it there? Or, what is a better way?

(After installation I would make a tar copy of that Python installation on HDD so that after rebooting all I would need to do would be untar it back to /dev/shm).

---

### Post by troymius on 2013-01-22
No comments? At least please tell me if the idea is completely... ehhh... not good? :-) Before I roll up my sleeves to do it...

---

### Post by Cheesemill on 2013-01-22
> **troymius said:**
> Now since python needs to be pulled from the hard-drive every time it's called, it slows things down
This shouldn't happen.
The first time a program is used it is loaded from the hard disk, but also cached in RAM.
All subsequent calls to python should then use this cached copy so it doesn't have to be loaded again.

For a simple intro on caching take a look at this article.

[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

---

### Post by troymius on 2013-01-22
Hi Cheesemill - thank you. I thought this should be happening most of the time but sometimes I would swear that Python is being loaded from HDD. Often enough to make it noticeable.

---

### Post by Cheesemill on 2013-01-22
How is your RAM usage?

Obviously applications will be dropped from the cache if memory is needed for other applications.

---

### Post by troymius on 2013-01-22
Sure. I don't fill the RAM anywhere near 50%. 

Is there a timeout for how long a program stays in RAM?

---

