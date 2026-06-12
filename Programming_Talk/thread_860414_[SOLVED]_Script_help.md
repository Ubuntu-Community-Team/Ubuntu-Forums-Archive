---
title: "[SOLVED] Script help"
date: 2008-07-15
forum: Programming Talk
---

### Post by dicecca112 on 2008-07-15
We have a machine here that I need to fill up 1.1 TB quick so that we can test our monitoring capability.  So I figured download Ubuntu DVD and fill up the partition that way.  Now I tried to write a script that would simply run through a while loop 300 times, and rename copy the file UbuntuDVD1, 2, 3 etc.  But it didn't work.  Can someone help me with this?

---

### Post by LaRoza on 2008-07-15
Why don't you just write a script to make large files?

---

### Post by dicecca112 on 2008-07-15
How do I do that?  Either way will work

---

### Post by drubin on 2008-07-15
> **LaRoza said:**
> Why don't you just write a script to make large files?

That seems to be the OP's question... 

I remember something about a a `dd` command that you could copy from /dev/zero or /dev/nrandom.

But you would have to google the exact place to copy form

---

### Post by drubin on 2008-07-15
> **dicecca112 said:**
> How do I do that?  Either way will work
[http://wiki.linuxquestions.org/wiki/Dd#Creating_empty_disk_images](http://wiki.linuxquestions.org/wiki/Dd#Creating_empty_disk_images) 
[http://maarten.lippmann.us/?page_id=116](http://maarten.lippmann.us/?page_id=116)

Try those for a starting point.

---

### Post by dicecca112 on 2008-07-15
totally forgot about dd, I know how to do it now, thanks guys

---

