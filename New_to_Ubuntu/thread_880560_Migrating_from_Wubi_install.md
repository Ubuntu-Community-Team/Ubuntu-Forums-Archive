---
title: "Migrating from Wubi install"
date: 2008-08-05
forum: New to Ubuntu
---

### Post by siddharthshukla on 2008-08-05
i switched a week back to ubuntu 8.04 and coz i was a complete newbie i chose to install ubuntu using wubi. Things have been running smoothly so far but the only problem is can't hibernate using a wubi install ,as i use a laptop i used to frequently hibernate in XP but miss that feature now, hence i thought of shifting to a complete ubuntu install on a seperate partition. I learnt about the LVPM tool from other threads but have certain doubts regarding them.

This is how my disk is partitioned: 
C:\ = 28GB Fat32 (windows installed here)  
D:\ = 40GB Fat32 
E:\ = 40GB Fat32
F:\ = 40GB NTFS(Wubi install here)

1.My doubt is do i need to use a tool and repartition one of the drives as extf3 and allot swap as instructed in the LVPM tutorial.

2. Also, when i did run LVPM it gave me 5 options for  a transfer
  a. sda1
  b. sda2
  c. sda5
  d. sda6
  e. sda7(not allowed coz wubi is installed)

How do i find out which drives these virtual devices are linked to as if i select any option randomly i will loose all the data in that partition. if i can find  a link between these virtual devices and the actual drives i can free a particular partition and transfer ubuntu on to that one without loosing any data. Please help me in this regard

---

### Post by fiddledd on 2008-08-05
No experience with LVPM, sorry. However I'd suggest you search these forums to see if Ubuntu supports suspend and hibernate on your laptop model first.

---

### Post by siddharthshukla on 2008-08-05
yes i gess ubuntu supports hibernation in my laptop model

---

