---
title: "install root and home on different drives"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by Billybob97060 on 2008-11-27
I'm not really sure how to go about this or if it even makes sense, but i have seen things in the past about installing the root files on one partition and all my other data on another so that when i upgrade i keep all my programs and things, is that possible?

---

### Post by ibuclaw on 2008-11-27
Yes, it is very possible and extremely elementary.

How much hard disk space do you have?
```
df -ha
```
```
sudo fdisk -l
```
Regards
Iain

---

### Post by Michael.Godawski on 2008-11-27
Yes, a separate home partition is possible:
Here a how-to to create a separate home after your installation:

[LIST]
[*][http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
[*]>>> and here how to plan your Ubuntu partitions:
[*][http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[/LIST]

---

### Post by nhasian on 2008-11-27
if your going to do a new install of Ubuntu then its quite a bit easier to put the / and /home on different partitions.  you can still do it after the install but its not so straight forward.

---

### Post by Billybob97060 on 2008-11-27
i've got an 80 gig drive for ubuntu, and if possible i'd rather not re-install unless there is an easy way to back up my programs and have it how i have it now after reinstallation, but whatever is going to be best in the long run i will go for

---

