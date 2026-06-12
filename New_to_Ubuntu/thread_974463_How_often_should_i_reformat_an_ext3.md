---
title: "How often should i reformat an ext3 ?"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by iKonaK on 2008-11-07
...or if is necessary to reformat an ext3 filesystem...
I asked because i herd some people talking on some sites that "is better for the hard drive to reformat once a year or so" ....
:) i'm writing this and it sounds "stupid", but i want to find more opinions...

---

### Post by scragar on 2008-11-07
I'm going to assume you mean defrag, and not reformat.

EXT3 is what is called a journaled file system, which is to say, as long as there is a bit of free space on the hard drive(about 20% is considered right, but depending on what you actualy do you can get away with 10% or even a bit lower) you won't generate gaps in files, which means ubuntu, for the most part, doesn't ever need de-fragmenting.

---

### Post by SunnyRabbiera on 2008-11-07
right, ext3 is a very solid system compared to NTFS

---

### Post by laurielegit on 2008-11-07
If you really what to defrag your filesystem then there is a tool called Shake ([http://vleu.net/shake/](http://vleu.net/shake/)). There isn't much need for it but it's a nice thing to know you have.

---

### Post by iKonaK on 2008-11-07
:lolflag: i have no intention defrag-ing an journaled file system, my question was about reformat-ing and if a reformat affects the life of a hard drive :popcorn:

---

### Post by scragar on 2008-11-08
Ooh, the busiest part of the hard drive is the little table of what is stored on it, which is wiped every time you reformat, which can only add to wear and tear on it... I can't imagine reformating would have any advantages to the life of the drive...

A much better way to increase the life of the drive would be to reduce it's temp, a slight reduction of a degree or 2 can increase lifetime of the drive by 10% or more, which can be quite a lot.

---

### Post by tahitiwibble on 2008-11-08
> **scragar said:**
> A much better way to increase the life of the drive would be to reduce it's temp, a slight reduction of a degree or 2 can increase lifetime of the drive by 10% or more, which can be quite a lot.

Oh dear :( that doesn't leave us much hope here in the non-air-conditioned (80° in the shade today) tropics.

---

### Post by ugm6hr on 2008-11-08
> **iKonaK said:**
> it sounds "stupid", but i want to find more opinions...

I agree with you.

---

### Post by psusi on 2008-11-09
Journaling has absolutely nothing to do with fragmentation.  Journaling is simply recording that you are going to make a change before you make it, then record that you finished the change, so that if the system crashes while making the change, when it comes up again it can quickly either finish or back out any changes that were in progress at the time to get the filesystem back to a consistent state without a full fsck.

For the original question, no, there is no benefit at all to reformatting, besides getting rid of any junk still laying around and starting fresh with little to no fragmentation.

---

### Post by Iowan on 2008-11-09
An occasional **fsck** probably isn't a bad thing - but it probably won't affect drive life either (not for better anyway).

---

