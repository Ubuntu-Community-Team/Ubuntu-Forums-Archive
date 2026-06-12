---
title: "Problem with partitioning during instal"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by keeferino on 2008-04-22
I'm currently running xp on my computer and I made the cd for ubuntu and I have rebooted using the cd. I click install and go through the first few questions and then I get to the partition section. I used the first option and had the division at about 50-50 and clicked continue. After a few moments an error box pops up and says that there was an error trying to write something to the disk. I'm not sure what the exact words are but I can easily find out if that would help. Any suggestions on what to do?

---

### Post by jken146 on 2008-04-22
What was the error?

---

### Post by mikeyphi on 2008-04-22
Before you try to install Ubuntu on your Windows Drive you should 'defrag' windows - at least twice!
Then there shouldn't be any random bits of data to conflict with the resizing option.

If that's not your problem - please ask again!

---

### Post by Jammy4041 on 2008-04-22
> **mikeyphi said:**
> Before you try to install Ubuntu on your Windows Drive you should 'defrag' windows - at least twice!
Then there shouldn't be any random bits of data to conflict with the resizing option.


Indeed, it is important to do this.

But the Ubuntu partitioner, is somewhat confusing. Without careful usage it can really mess up your system. 

So, what do you do?

This is what I did, I used Gparted.

So, you will need your Live Desktop CD handy. Boot from the Live CD, and you will see the Ubuntu desktop. THEN **DO NOT** CLICK INSTALL.  

Go to System..>Administration..>gParted (It might be named as Partition Editor). If it isn't there, go to Add Remove software (don't worry, all the software is on the CD, so you won't need an internet connection for this bit).

OK, with gParted (Partition Editor) open, it's time to resize your partition. You will see a big bar going accross the top on the screen. Right click on this bar and click resize move. Shrink it down so it's a bit smaller- gParted will not even let you go so small that you lose some files, (unless you destroy the partition, which is of course, NOT what you want to do.

When you have done this, you should see, appearing as if by magic on the right, a shaded area of unallocated space.

This is where your Ubuntu partition will go.

If you make mistake, click undo. You haven't done anything to your hard drive until you press apply. So click Apply, and, depending on the size of your hard drive, ram, processor speed, etc, you may have to wait a while before it finishes.

When gParted has finished, run the instller, as you did, UNTIL you get to the partioner. Then at theis screen select

```
Guided-Use Largest Continous Free Space
```

This will install Ubuntu in that unallocated free space.

Then, run through the rest of the installer.

---

