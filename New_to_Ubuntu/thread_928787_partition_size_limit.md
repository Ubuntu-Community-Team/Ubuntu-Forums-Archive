---
title: "partition size limit?"
date: 2008-09-24
forum: New to Ubuntu
---

### Post by gregorio on 2008-09-24
I was asked this question by someone curious about linux.  He mentioned that XP has limits to the size of partitions on the hard drive and asked what the limits were for linux.  Myself, I haven't a clue, but knew where to ask.  So, I'm asking.

Thanks

---

### Post by Paqman on 2008-09-24
AFAIK the only limit on the size of any one partition is the max size for that filesystem, which is a purely academic limit since you can't buy a hard drive big enough use it all up. Of more relevance to most users is the limit on the *number* of partitions, however. You can only have four primary partitions.

The way to get around this is for one of the partitions to be a special type of partition called an extended partition. An extended partition can contain other partitions nested inside it.

---

### Post by gregorio on 2008-09-24
this forum is too cool. Ask a question, and within 3 minutes, have my answer.

Thanks again!

---

### Post by aeiah on 2008-09-24
max sizes: 

FAT32 (used to be used in windows): 8TB
NTFS (what windows uses now): 16EB
Ext3 (what you'll probably use on linux): 32TB

so in reality there is no limit. unless you've got a hell of a lot of hard drives in a raid array.

---

### Post by Paqman on 2008-09-24
> **aeiah said:**
> 
Ext3 (what you'll probably use on linux): 32TB


We'll probably have hard drives that big available in about 6 years (according to Mr Moore), but by then we should have Ext4.

---

