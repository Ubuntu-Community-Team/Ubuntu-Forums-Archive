---
title: "Installing Ubuntu with Vista"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by rohitsb on 2008-06-19
Hello,

So I've tried Wubi for around 2 months now and feel that I'm ready to start on a complete Linux installation. Steps that I've completed so far:

1. In Vista->My Computer->Manage->Storage, I shrank the D: by about 18 GBs.

2. Booted the Ubuntu 8.04 Live CD and came to the partitions screen

And this is where I ran into problems. I did not get the "Guided - Use largest contiguous free space option". So I went into "Manual" mode. My unallocated space shows up there, but it is marked "unusable".

Any hints on how to proceed ? Defragmentation was suggested on other threads, but I let it run for about 20 mints and no change. 

Regards

RSB

---

### Post by Dynaflow on 2008-06-19
Did it allow you to check a box under "Format?" in the manual partitioner?  

Personally, I would allow Vista to re-expand that partition and then let Hardy do its own thing in its installer.  See here for a tutorial:  [http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

---

### Post by rohitsb on 2008-06-19
Hello,

No it didn't allow me to do select the "unusable" space at all. I'll do as suggested in the link provided and report back if it works.

---

### Post by sam_delta on 2008-06-19
thats because you already have 4 primary partitions, you will need to delete one of the primary and convert it to a extended partition , and then, you will be able to use the unallocated to make another extended partion

the thing is, you can only have 4 primary partitions, or 3 primary and 1 extended (the extended partition can contain more extended partitions inside.) so practically, you can have 3 pramary and infinite extended partitions

any question, please ask
sam

---

### Post by rohitsb on 2008-06-19
> **sam_delta said:**
> thats because you already have 4 primary partitions, you will need to delete one of the primary and convert it to a extended partition , and then, you will be able to use the unallocated to make another extended partion

the thing is, you can only have 4 primary partitions, or 3 primary and 1 extended (the extended partition can contain more extended partitions inside.) so practically, you can have 3 pramary and infinite extended partitions

any question, please ask
sam

Wait a sec. Let me understand this:

Under Vista (My Comp->Manage->Storage), I see the following:
1. EISA1 (EISA config)
2. ACER (C: - Primary, System, Boot, Page)
3. DATA (D: - Primary)
4. EISA2 (EISA config)

EISA1 is Vista recovery and EISA2 is Acer media partition. Counting C: and D:, there are only 2 primary partitions right ? So why does Linux see 4 ?

But in response to your suggestion, is there any way to convert the primary partition to an extended one ? Or do I have to delete the second primary (D: ) altogether ? If so, is there any link that I can refer to ?

Thanks & Regards

RSB

---

### Post by sam_delta on 2008-06-20
> **rohitsb said:**
> Wait a sec. Let me understand this:

Under Vista (My Comp->Manage->Storage), I see the following:
1. EISA1 (EISA config)
2. ACER (C: - Primary, System, Boot, Page)
3. DATA (D: - Primary)
4. EISA2 (EISA config)

EISA1 is Vista recovery and EISA2 is Acer media partition. Counting C: and D:, there are only 2 primary partitions right ? So why does Linux see 4 ?

But in response to your suggestion, is there any way to convert the primary partition to an extended one ? Or do I have to delete the second primary (D: ) altogether ? If so, is there any link that I can refer to ?

Thanks & Regards

RSB
EISA1 and EISA2 are also considered primary partitions.., there are just 2 types of partitions , primaries/logicals, and extended

you can only have 4 primaries, or 3 primaries and 1 extended (the extended can be made of as much logical partitins as you can) so in simple words:
you can have 4 primaries, but there will be no room for extendeds, or you can have 3 primaries and as much extended as you like in the "4 slot"

what i would recomend is to backup all your data on your D: drive, remove that partition and make a new extended partition then, copy your backed up data from your D drive back to its new extended partition. then, youll have 3 primary and 1 extended, so having just 3 primary partitions, you still have space for infinite logical partitions inside that 4rth extended partition (duno if i explain myself clear)

hope it helps
any question, please ask
sam

---

### Post by Dynaflow on 2008-06-20
> **sam_delta said:**
> thats because you already have 4 primary partitions, you will need to delete one of the primary and convert it to a extended partition , and then, you will be able to use the unallocated to make another extended partion


[slaps forehead]  Derp.  Of course.  I had a similar problem with a couple laptops I "Linuxed" last year, and what I did was zap the recovery partitions, because they were more or less redundant once I had burned sets of recovery CDs for each machine.  

Here is some info about those recovery partitions:  [http://www.mydigitallife.info/2008/02/29/delete-and-remove-to-unlock-eisa-hidden-recovery-or-diagnostic-partition-in-vista/](http://www.mydigitallife.info/2008/02/29/delete-and-remove-to-unlock-eisa-hidden-recovery-or-diagnostic-partition-in-vista/)

Make sure you have a set of physical recovery CDs before you delete any patitions, because if/when Windows goes on the fritz, you'll need them to recover Windows.  You won't be able to restore it off the drive anymore, and I think your ability to make recovery CDs also leaves with those partitions.

---

### Post by Victormd on 2008-06-20
> **sam_delta said:**
> 
...


+1

Also, +1 for Dynaflow.
Create the recovery CDs/DVDs and get rid of the recovery partitions (that you can). They're probably ~8GBs each anyway so that's what you'll need to install Ubuntu.

---

### Post by rohitsb on 2008-06-20
Hello,

Thx for the info. I would like to keep my hard disk partition structure as close to the manufacturer's as possible. I remember reading somewhere that if you try to restore from the CDs, the hard disk goes back to the same state.

Anyways, as suggested, I'll create a backup of my system. Does anyone know of any link/utility that will tell me how to delete D: and re-create it as extended partition ? Currently, I do not have any data on D:.

Many thanks

RSB

---

### Post by rohitsb on 2008-06-20
12-hr bump coming up.

Can anyone provide a step-by-step to deleting a primary partition and re-creating it as extended partition ?

Much appreciated

RSB

---

### Post by sam_delta on 2008-06-20
in the live cd,  lauch gparted by clicking ALT-F2 then typing
```
gksudo gparted
``` (you can also use the menu, but i dont remember where gparted is placed)

then, will will have a graphical interface where you can select the partition and click on "delete", and add a new one as extended

any questions, please ask
sam

---

