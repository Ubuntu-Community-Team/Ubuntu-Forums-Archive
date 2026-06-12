---
title: "Goofed up on making install partitions"
date: 2016-04-23
forum: New to Ubuntu
---

### Post by crip720 on 2016-04-23
I recently did a clean install of 16.04beta, but have found out that I goofed up on making my /home partition.  Ubuntu is only using  / as the only partition.  I think my problem is that /home is not an extended partition.  Can I change this now safely or should I do clean install again?  Can you also suggest how to create / and /home partitions? I added two screenshots from Disks, so you can see what I did.  Thank you.

---

### Post by Impavidus on 2016-04-23
I take it that sda7 is your root partition and you want to use sda9 as your /home partition? That is easy. The partition type is OK. Extended partitions are not applicable here, as this is GPT partitioning. Use this tutorial: [https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving). You can skip step 1 as you already have your partition ready.

---

### Post by crip720 on 2016-04-23
Is this safe to do from install or should I do it from live DVD?  I have intel baytrail hardware, install has been fixed, but do not know how long Live DVD will be stable.

---

### Post by Geoffrey_Arndt on 2016-04-23
Simplest to use Live DVD.   If that were my system, I'd reinstall with no separate /home  partition.   On a 5 year LTS, I see no remarkable advantage (as presumably, you won't be doing reinstalls every 6-9 months).    But a minimum I'd give Ubuntu is 80 GiB, and preferably more (like 120gb or 150) for expansion.    So, all you really need is a root (/) and a swap (in addition to the Windows cruft).

---

### Post by grahammechanical on 2016-04-23
I do not have a separate /home partition and I do switch Ubuntu versions every six months but I keep all my data in a separate partition. Then when I re-install I never over-write that "data" partition. So, the choice comes down to separate /home partition or separate data partition. It is your choice.

Regards.

---

### Post by Impavidus on 2016-04-24
I once used the linked instructions to create a /home partition from my installed system, without using a live disk (except beforehand, to create the partition). It worked flawlessly.

---

### Post by crip720 on 2016-04-24
Thank you. Going to back up first and then do.  Colin.

---

