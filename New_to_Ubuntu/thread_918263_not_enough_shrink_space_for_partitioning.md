---
title: "not enough shrink space for partitioning"
date: 2008-09-12
forum: New to Ubuntu
---

### Post by punkbohemian on 2008-09-12
I'm following _[this guide]("http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=2")_ so I can dual-boot Vista and Ubuntu. When I try to shrink Vista's partition, it's not letting me shrink it by much. Apparently, it will only let me create a ~50GB partition, which doesn't make sense as it's a 160GB HD and I'm only using about 30GB of it (with another 12GB reserved as a system recovery partition).

I've already done a defrag (figuring it will free up more continuous space), but having to reserve ~85GB for ~40GB of data is wasting more space than I would like. And while ~50GB is enough for Ubuntu, I'd like to dedicate more space to that partition.

Is it possible, or do I just need to suck it up and deal with only having 50GB for Ubuntu?

---

### Post by ordaide on 2008-09-12
TRY -*

1. Press Win+R to open the run box
2. Type in diskmgmt.msc and click OK
3. Press the Continue button if you need to grant permission
4. Right-click on the partition you wish to shrink
5. Select Shrink Volume...
6. Select your settings and click the Shrink button

Unless you did already :)

If so -

Defrag again and then temporarily turn off System Restore, do the shrink and turn System Restore back on.

---

### Post by punkbohemian on 2008-09-13
I did all that, and it didn't free up any space. In fact, it's only a day later and I went into disk management again, and now I can free up 10GB **less** space than the day before. I haven't even done anything on my computer since then...

---

### Post by bodhi.zazen on 2008-09-13
> **punkbohemian said:**
> I'm following _[this guide]("http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=2")_ so I can dual-boot Vista and Ubuntu. When I try to shrink Vista's partition, it's not letting me shrink it by much. Apparently, it will only let me create a ~50GB partition, which doesn't make sense as it's a 160GB HD and I'm only using about 30GB of it (with another 12GB reserved as a system recovery partition).

I've already done a defrag (figuring it will free up more continuous space), but having to reserve ~85GB for ~40GB of data is wasting more space than I would like. And while ~50GB is enough for Ubuntu, I'd like to dedicate more space to that partition.

Is it possible, or do I just need to suck it up and deal with only having 50GB for Ubuntu?

The vista partition manager is a very blunt tool.

Back up your date, defragment your HD (from vista), then boot the Ubuntu desktop cd and use gparted.

---

