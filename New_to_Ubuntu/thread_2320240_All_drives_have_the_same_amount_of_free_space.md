---
title: "All drives have the same amount of free space"
date: 2016-04-11
forum: New to Ubuntu
---

### Post by martin196 on 2016-04-11
I seem to have an issue that is affecting all of my Shares.
I have quite a few varying size physical drives installed in my Ubuntu 14.04 box (basically put in everything I had to create my server)
I have created shares of the Drives rather than Partitions.

The strange thing is that when I try to write anything to any of the shares, the maximum free space is always the same. (31GB or so). What seems to be happening is that the files are being copied to the OS drive, rather than the actual shared drive since I get a disk space warning if I copy the full amount of data over.

I've searched for a couple of evenings now and have run out of different ways to describe the issue.

I'm new to Ubuntu, so...
Any help gratefully appreciated.

---

### Post by papibe on 2016-04-11
Hi martin196. Welcome to the forum ):P

Do you mean samba shares? or something else?

Could you open a terminal run these commands and post back the results? (you can copy/paste the text from the terminal)
```
mount -l

df -h

df -i

sudo fdisl -l
```
Regards.

---

