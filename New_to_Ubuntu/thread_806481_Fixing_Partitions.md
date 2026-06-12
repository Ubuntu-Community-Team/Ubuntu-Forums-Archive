---
title: "Fixing Partitions"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by melrom on 2008-05-25
When I installed Hardy off of CD, it installed itself as sda7 with sda8 as swap, while Gutsy stayed on ext5 with ext6 as swap, but if I go into gparted, I can't delete 5 and 6, because it says there are higher numbers than it. Would it work if I tried to delete them from a live CD??

---

### Post by Ericyzfr1 on 2008-05-25
I don't think you would be able to modify your partitions from a live CD since a live CD does not have write access to them.

---

### Post by Bakon Jarser on 2008-05-25
Live cd should have write access and I think you can delete them from there.

---

### Post by wolfen69 on 2008-05-25
pop in live cd, install gparted.then:
```
sudo su
```then
```
gparted
```you will then be able to delete partitions

---

### Post by Bakon Jarser on 2008-05-25
> **wolfen69 said:**
> pop in live cd, install gparted.then:
```
sudo su
```then
```
gparted
```you will then be able to delete partitions

Don't you need to unmount them first?  Might be safer to use the live cd.

---

### Post by Tatty on 2008-05-25
> **Bakon Jarser said:**
> Don't you need to unmount them first?  Might be safer to use the live cd.

He said that...
> **wolfen69 said:**
> pop in live cd

lol ;)

@melrom

AFAIK You cant alter the partitions on a mounted drive so you will have to use a live cd.

Gparted is installed by default on the live cd, find it in System->Administration->Partition Editor

---

### Post by melrom on 2008-05-25
yeah i know gparted is on the live cd. lol. thanks. i'll do it from there.

---

### Post by Bakon Jarser on 2008-05-25
> **Tatty said:**
> He said that...

Leave my alone.  I failed reading comprehension in school! :)

---

### Post by wolfen69 on 2008-05-25
gparted does not come with hardy. use a gutsy cd if you have one. and yes, you must unmount the partitions first.

---

### Post by Tatty on 2008-05-25
> **wolfen69 said:**
> gparted does not come with hardy. use a gutsy cd if you have one. and yes, you must unmount the partitions first.

Are you sure?  Its definitely on the hardy amd64 live cd, I have used it today to format a drive

:)

---

### Post by melrom on 2008-05-26
i'm pretty sure gparted is on my hardy live cd too...

---

