---
title: "Free memory space for quicker response"
date: 2013-07-06
forum: New to Ubuntu
---

### Post by Hankbonk on 2013-07-06
I'm running ubuntu 9.04 on a very old and small PC .  I know one can kill processes in the System Monitor, but I have got no clue to which processes can be killed without running into trouble . Anyone some advice ?

---

### Post by prodigy_ on 2013-07-06
You can use something like ```
ps -eo uid,pid,command,rss c k-rss
``` in terminal to sort processes by RAM usage. Anything running under UID <1000 is probably a system process.

However, Ubuntu 9.04 has been obsolete for quite some time. Unless you're positively certain you need it, you should install a current version of some lightweight distro. Lubuntu, Xubuntu and Mint/Xfce are good candidates. Also, slow response isn't always caused by lack of memory. Use ```
watch free -m
``` command to check if swap is being actively used. If it's not, freeing memory probably won't do you any good.

---

### Post by Hankbonk on 2013-07-06
Thanks for your quick reply, Prodigy .

So if I get it right, everything in that ps list with an UID less than value of '1000' I certainly should NOT kill, because it's a system process ?

Swapping is used .

I'm awaiting your answer, thanks in advance !

---

### Post by Shishimaru on 2013-07-06
I'd use Lubuntu 13.04 and install zram-config. I have zram on my Ubuntu 13.04 and it does help freeing RAM.

---

### Post by prodigy_ on 2013-07-06
> **Hankbonk said:**
> So if I get it right, everything in that ps list with an UID less than value of '1000' I certainly should NOT kill, because it's a system process ?
Mostly. There are exceptions (for instance, on my laptop transmission-daemon runs as UID 118 but it's actually a BitTorrent client, not a system service) but it's a good general rule.

Still, unless there's a memory leak somewhere, killing processes isn't going to help you all that much. In the long run, if your computer runs too slow, you have two options: 
- lighten the load: switch to a lighter DE and, possibly, compile a custom kernel with everything unnecessary disabled (the latter can take quite some time as it's mostly trial and error);
- upgrade: add more RAM or maybe even replace the whole thing.

---

