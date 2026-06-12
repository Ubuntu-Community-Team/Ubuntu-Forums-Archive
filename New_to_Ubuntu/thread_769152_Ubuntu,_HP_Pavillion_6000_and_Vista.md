---
title: "Ubuntu, HP Pavillion 6000 and Vista"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by yc2 on 2008-04-26
Hello,

I am considering installing Ubuntu on my laptop. I just bought a HP pavillion DV6751.eo, nVidia 8400, Conexant HD Smart Audio 221, Win Vista OEM 32 bit.

It has two partitions: C: 190GB free / 223 GB, D: 10GB recovery partition.

I want to set up a small Ubuntu system of about 10-15 GB, desktop environment and maybe webserver. Dualboot Win Vista and Ubuntu.

I have burnt the two HP recovery DVD disks.

This is the only computer I have access to right now and I really need the Vista system to work perfectly until the Ubuntu system is tried out thoroughly. So my question is related to trying to anticipate what could go wrong.

There are so many things I have heard but could not verify. (Like HP 6000 series was not good with Gutsy, GParted has problem with Vista, my laptop har probably SATA-connected disk ...)

I have tried the Hardy Live CD quickly, it seems to work, I can surf, but f.ex. I cannot hear any sound.

My plan is to shrink the C partition (using Vista disk handler) by 10 GB and make one 9 GB (root) and one 1G (swap) partition. Then somehow using the "manual partitioning" option installing Hardy. (I think there is an install option in the boot menu of Hardy, not only the desktop icon "install to HD"?)

I have also heard that repartitioning (like shrinking the C partition) will make the HP-recovery function (pressing f11) from the D partition useless. In that case it would be better to somehow remove the D-partition first since it is useless, or maybe direcly use its 10 GB for Ubuntu?

However, most importantly, if something goes wrong I MUST ABSOLUTELY be able to set up the original Win Vista system quickly on this, my only computer. As I understand the HP recovery DVDs that I have burnt will be able to do restore my system no matter how I have repartitioned or otherwise changed the information on the HDD.

So please tell me, does this plan seem like a good one and does it have enough "plan B" coverage ;)

Thanks :popcorn:

---

### Post by itix on 2008-05-11
Ser att du är svensk, men tar det på engelska så att andra i din situation kan hitta tråden och läsa.

If you are going to delete the recovery partition, do so with GParted. I can almost guarantee that deleting that one won't affect the other partitions. The problems I've heard of (with GParted and vista) is that it can't shrink partitions. Deleting recovery should be no biggie.

I don't know how vista disk handler works but if it works anything similar to GParted on Ubuntu, I'd guess it leaves the leftover bits from the shrunk partition as free space. Ubuntu gives you the opportunity to install on "the largest continuous free space" which would be your option of favor since the vista-developer hopefully had some sort of brains and designed the system to leave the leftover space empty.

In any case, use the "install on largest continuous space"-option.

Then about the webserver deal... you know that that server only will be available when your ubuntu partition is running right??

As a conclusion, I must say you seam to be quite well prepared. Just make sure that you have any valuable data backed up (like bank ID's, office documents, work related stuff, personal photos etc) just in case. 2 DVDs seam awfully small to restore a system of over 30 GB.

I wrecked my windows install the first time I tried dual booting. I shrunk that one though but I had everything backed up so it was just for me to reinstall everything. If so, remember to install windows first because windows disables the ubuntu partition...

---

