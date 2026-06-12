---
title: "Would this partition configuration work well with Sabayon?"
date: 2008-09-05
forum: Other OS Talk
---

### Post by Timberwolf5578 on 2008-09-05
I already have WinXP on one parition of my system. I have a 500gb hard drive and I give 50% to WinXP and 50% to whichever Linux distro I use. In past installations of distros (Mandriva, SUSE, Ubuntu, Mint) I used the following partitions. And I wanted to know if this partition configuration would work well with Sabayon too:

sda5 - 20gb ext3 /
sda 6 - 2gb SWAP
sda 7 - 210gb ext3 /home

In other distros I used, I was told this is the best way to partition my hard drive because it makes upgrades easier. Is this also the best way to partition for Sab?

Any responses will be appreciated.

Thanks :)

---

### Post by handy on 2008-09-05
If you have 1Gb of RAM or more, I wouldn't bother with a swap partition, unless you record edit movies &/or multitrack audio, or you are into CAD & 3D rendering.

20Gb / should be plenty, you can always resize your partitions later anyway.

I use ext3 for /, & JFS for /home.

---

### Post by Timberwolf5578 on 2008-09-05
> **handy said:**
> If you have 1Gb of RAM or more, I wouldn't bother with a swap partition, unless you record edit movies &/or multitrack audio, or you are into CAD & 3D rendering.

20Gb / should be plenty, you can always resize your partitions later anyway.

I use ext3 for /, & JFS for /home.

Why JFS for /home ?

I have been using ext3 for /home with all the other distros I tried (Ubuntu, Mint, Mandriva, SUSE).

---

### Post by wolfen69 on 2008-09-05
using JFS is just a personal preference, as is partitioning. i **never** keep anything of value on my ubuntu install and keep all my files on seperate hard drives. that means i dont need a seperate home folder. the only things in my home folder i backup are .mozilla and .thunderbird. it makes things very simple and easy.

---

### Post by handy on 2008-09-05
> **Timberwolf5578 said:**
> Why JFS for /home ?

I have been using ext3 for /home with all the other distros I tried (Ubuntu, Mint, Mandriva, SUSE).

[***_JFS_***]("http://en.wikipedia.org/wiki/IBM_Journaled_File_System_2_(JFS2)") in theory is faster than ext3, & is also secure.

---

