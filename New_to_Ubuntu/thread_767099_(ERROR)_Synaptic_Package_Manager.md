---
title: "(ERROR) Synaptic Package Manager"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by gav-the-lad on 2008-04-25
Hi all, total noob here in need of some help. I have tride to access synaptic but receive the message:
[COLOR="Red"]"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."[/COLOR] 

The reason i am accessing  synaptic is because i am unable to view certain sites with flash player, like myspace, bbc iplayer, youtube, and i wanted to make sure i had the correct pluggin installed.

Any help or advice would be much appriciated

---

### Post by TeoBigusGeekus on 2008-04-25
Well, open up a terminal and type
```
sudo dpkg --configure -a
```

---

### Post by overdrank on 2008-04-25
> **gav-the-lad said:**
> Hi all, total noob here in need of some help. I have tride to access synaptic but receive the message:
[COLOR="Red"]"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."[/COLOR] 

The reason i am accessing  synaptic is because i am unable to view certain sites with flash player, like myspace, bbc iplayer, youtube, and i wanted to make sure i had the correct pluggin installed.

Any help or advice would be much appriciated

HI and welcome, You need to run that command in the terminal 
```
sudo dpkg --configure -a
``` the terminal is located under applications, accessories.

---

### Post by gav-the-lad on 2008-04-25
Thanks for pointing me in the right direction guys:) i had a feeling it would be something obvious. Yeah I'm a noob :lolflag:

---

### Post by overdrank on 2008-04-25
> **gav-the-lad said:**
> Thanks for pointing me in the right direction guys:) i had a feeling it would be something obvious. Yeah I'm a noob :lolflag:

No problem and welcome again, a search of the forums reveals so much. :popcorn:

---

