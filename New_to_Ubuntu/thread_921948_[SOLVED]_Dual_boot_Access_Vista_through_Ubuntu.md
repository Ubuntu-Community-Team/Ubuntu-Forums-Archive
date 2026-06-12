---
title: "[SOLVED] Dual boot: Access Vista through Ubuntu"
date: 2008-09-16
forum: New to Ubuntu
---

### Post by JKSnort on 2008-09-16
So pretty much I just used, Webi, to installed Ubuntu onto my computer, now I want to use it to get internet access over wifi.

I think I know which files to download, but I doesn't know how I would access them from Ubuntu?

I have this run on a partitioned drive.

[B]So how do i access files in my vista, from Ubuntu?
or should I say how do I mount Vista on Ubuntu?[/B]

And I have A Boardband BCM4130 rev 01 card?
 will this be the right download?

wget [http://myspamb8.googlepages.com/R174291-pruned.zip](http://myspamb8.googlepages.com/R174291-pruned.zip)
unzip R174291-pruned.zip

one more thing: does using Webi to install Ubuntu, slow anything down?

Thanx

---

### Post by darrelljon on 2008-09-17
1. I don't think Dual boot is the same as WUBI
2. If you installed a dual boot, your Windows partition is under /mnt
3. I think a WUBI install is done on a NTFS partition without changing any partitions
4. Before you download drivers for wireless check if your card is already detected (type iwconfig into the terminal).
5. A WUBI install may be marginally slower than a traditional install.

---

