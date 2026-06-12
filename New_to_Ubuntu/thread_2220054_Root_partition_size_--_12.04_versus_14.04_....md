---
title: "Root partition size -- 12.04 versus 14.04 ..."
date: 2014-04-26
forum: New to Ubuntu
---

### Post by cwmoser on 2014-04-26
I just migrated from Ubuntu 12.04 to 14.04.
I have 12.04 root in partition /dev/sda4 and 14.04 in /dev/sda1
My /home is in another partition /dev/sda3.

I think I have installed every applicationin 14.04 that I had in 12.04.
What has caught my attention is that the space used by root
14.04 is 6.3GB while with 12.04 the space used by root is 13GB.

Just before installing 14.04 I had searched for ways to clean up the root partition
and was able to reduce the utilized space by a few hundred KBs.

Why is this that my 14.04 is less than half the size in 12.04?  
Does the utilized space in the root partition increase over time?
I did a search for large files in 12.04 and did not find any that would be the reason
for the 13GB used space.

---

### Post by pfeiffep on 2014-04-26
Just a thought - old linux kernels???

---

### Post by Impavidus on 2014-04-26
If you never cleaned old kernels you may have collected a lot of them in /boot. Have a look there.

To prevent the same from happening in 14.04, run **sudo apt-get autoremove** occasionaly.

---

### Post by LastDino on 2014-04-26
Kernals, Cache, Unused packages, removed software packages and thumbnail cache. All this can really gather themselves over longer period of times. Although,  I usually stay away from cleaners, its a good idea to clean all that manually in interval of few months.
[h=2][/h][h=2][/h]

---

### Post by cwmoser on 2014-04-26
Only have 2 kernels in /boot on my Ubuntu 12.04 - all the files in /boot total less than 500MB.

Curiosity has me perplexed.

---

