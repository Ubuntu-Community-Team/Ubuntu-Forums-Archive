---
title: "browsers use 100% cpu"
date: 2017-04-20
forum: New to Ubuntu
---

### Post by astroni on 2017-04-20
Hi, I have an old pc (pentuim 4, 1.7GB RAM, 160GB HDD) in wich I installed lubuntu.
the problem is that it uses 100% of the cpu when I use a browser (chromium or firefox). I mad the swappiness 10 and updated but the problem persists. I read lots of the articles related to this problem but none of them seems to work for me. I think that's it's related to some misconfiguration since I used to run the same programmes on windows XP.
any help would appreciated.

---

### Post by wildmanne39 on 2017-04-20
What version of firefox are you using? this may give a clue.
[https://ubuntuforums.org/showthread.php?t=2359010](https://ubuntuforums.org/showthread.php?t=2359010)

You have to remember windows xp is a very old system, and you installed a new version of lubuntu so it is going to take more resources then xp.

What version of lubuntu did you install, in 17.04 swap partitions have been done away with and a swap file is now being used.

You could also do a minimal install and that would be easier on resources.

---

### Post by wildmanne39 on 2017-04-20
*Thread moved to **New to Ubuntu**.*

---

### Post by astroni on 2017-04-20
I'm using lubuntu 16.10 and I'm not sure how I can do a minimal install. I forgot to mention that only 700MB/1700MB RAM is used
thanks for your reply

---

### Post by Impavidus on 2017-04-20
You can check memory usage with **free -m** or with **top**. See if swap is used. Actually, the default swappiness is quite good. Reducing swappiness makes the system resort to swap later, but early swapping (when there's time to write unused stuff to disk, instead of right when the extra memory is required) may not be too bad.

But swap has to do with disk activity. You complain about CPU activity. Use **top** to see which program causes the problem. Try disabling some add-ons or extensions of your web browsers. One of the reasons I keep flash disabled most of the time is to reduce fan noise.

---

