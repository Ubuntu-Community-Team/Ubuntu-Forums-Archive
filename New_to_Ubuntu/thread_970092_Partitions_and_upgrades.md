---
title: "Partitions and upgrades"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by Russell Herin on 2008-11-03
I haven't installed anything yet, since I'm doing research on all this.  I was reading up on using partitions for system files and the like.  I know that, for example, putting /boot on its own partition will cause problems with upgrading.

What about other uses of partition?  If I put /usr, /var, /tmp, /usr/local, and /home on partitions, which will cause issues when upgrading?  I don't plan on using a separate /boot; but /home for sure (which I know is just A-Okay).

I'm using xubuntu, by the way, but I guess it doesn't matter.

---

### Post by louieb on 2008-11-03
Because Ubuntu Linux brings out a new release  2 times a year I like to have my data on a different partition from the OS. having a separate /home is one way to do that. I like my data such as photos and  music, on its own partition also..  
So the PCs I've set up generally have 4 partitions.


[LIST]
[*]/  (root)  7-15GB If you burn DVDs go with the larger ortwise 7-10GB is plenty
[*]/home 1-2GB user configuration files mostly (email is largest space user)
[*]/media/data  photos, music whatever. Gets all the space I can give it.
[*]swap .5GB is plenty, unless you hibernate the computer then  larger that the amout of ram. My laptop with 1GB ram has a 1.2GB swap. Hibernates with no problems.
[/LIST]

---

### Post by diskotek on 2008-11-29
so how to name that partition which we will use for data/music storage? i always make mistake about it when i'm making a fresh install. last time i made it /usr/local :( how should i connect it, with which label?

---

