---
title: "[SOLVED] A quick question about re-sizing a partition"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by drjonze on 2008-06-27
Hi,

I am going to re-size the partition that has Vista on it, I want a little more room for ubuntu. My question is: Lets say my windows partition is 100GB's but I'm only using 50GB's. If I resized it to 60GB's to free up 40 more (and assuming that I defraged the hard drive first!) would it just 'chop off' the unused space from the partition, leaving my current windows install completely intact or will it reformat and make me re-install?

---

### Post by Duck2006 on 2008-06-27
> **drjonze said:**
> Hi,

I am going to re-size the partition that has Vista on it, I want a little more room for ubuntu. My question is: Lets say my windows partition is 100GB's but I'm only using 50GB's. If I resized it to 60GB's to free up 40 more (and assuming that I defraged the hard drive first!) would it just 'chop off' the unused space from the partition, leaving my current windows install completely intact or will it reformat and make me re-install?

Use the partition tool within vista to give you more room for your ubuntu install, then add the new space to your ubuntu partition using, gparted or parted magic live cd.

---

### Post by snowpine on 2008-06-27
> **drjonze said:**
> Hi,

I am going to re-size the partition that has Vista on it, I want a little more room for ubuntu. My question is: Lets say my windows partition is 100GB's but I'm only using 50GB's. If I resized it to 60GB's to free up 40 more (and assuming that I defraged the hard drive first!) would it just 'chop off' the unused space from the partition, leaving my current windows install completely intact or will it reformat and make me re-install?

Hi Dr. Jonze,

The word on the street is that you should use Vista's own utilities to re-size the partition, rather than let Ubuntu do it. Hypothetically, Vista should survive this operation with no problem, but then again, this is an Ubuntu forum, not a Vista forum, now isn't it! :)

And as always, you should back up your data before messing with partitions. Good luck!

---

### Post by drjonze on 2008-06-27
> **snowpine said:**
> Hi Dr. Jonze,

The word on the street is that you should use Vista's own utilities to re-size the partition, rather than let Ubuntu do it. Hypothetically, Vista should survive this operation with no problem, but then again, this is an Ubuntu forum, not a Vista forum, now isn't it! :)

And as always, you should back up your data before messing with partitions. Good luck!

Thanks,I have seen the Vista partition tool before, I'll use that for sure. 
I don't really care if Vista gets blown away as I don't use it and all my data has been migrated to ubuntu already. I just want to have it 'just in case' and I'm hoping to not have to re-install it out of laziness. :)

---

### Post by youthforlinux on 2008-06-27
I've had a couple of times in Vista where it decided that I didn't have enought space to resize it...then I used gparted...one time it worked and the other time it didn't....be sure to backup....

---

