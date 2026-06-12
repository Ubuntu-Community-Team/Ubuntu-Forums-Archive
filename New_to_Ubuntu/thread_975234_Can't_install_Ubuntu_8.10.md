---
title: "Can't install Ubuntu 8.10"
date: 2008-11-08
forum: New to Ubuntu
---

### Post by Abhishek_12 on 2008-11-08
Hello Everyone

I'm having a problem while installing Ubuntu 8.10 . I'm quite new to linux so I'm very srry if what I'm about to ask is very stupid and rhetoric .

My pc configuration is like this

Total 160 gb hard drive
Nvidia gforce etc.

Window xp is already installed in it 
 
I have created ext < ext# and swap partitions using partition magic

[B]_Here's what my problem is _

When i tried to install Ubuntu 8.10 from live cd  on to the above partitions . I couldn't go beyond screen 4 i.e No partitions were visible there.      [/B]

please advise as it is getting quite frustrating  and I really want to try 8.10 out

---

### Post by Abhishek_12 on 2008-11-08
I have read release notes and i think this is mentioned in it but It'd be really helpful to tell me how to go around this

---

### Post by Abhishek_12 on 2008-11-08
Hello Everyone

I'm having a problem while installing Ubuntu 8.10 . I'm quite new to linux so I'm very srry if what I'm about to ask is very stupid and rhetoric .

My pc configuration is like this

Total 160 gb hard drive
Nvidia gforce etc.

Window xp is already installed in it 
 
I have created ext < ext# and swap partitions using partition magic

[B]_Here's what my problem is _


PS: To moderators I'm srry for posting this in multiple forums as I thought it can be put in either of them

When i tried to install Ubuntu 8.10 from live cd  on to the above partitions . I couldn't go beyond screen 4 i.e No partitions were visible there.      [/B]

Now I know this kinda thing was mentioned in release notes . It'd have been much better if a work around was posted along with that . So that noob like me  don't get frustrated by this.

I really want to use ubuntu 8.10 so please help me :(


please advise as it is getting quite frustrating  and I really want to try 8.10 out

---

### Post by overdrank on 2008-11-08
> **Abhishek_12 said:**
> Hello Everyone

PS: To moderators I'm srry for posting this in multiple forums as I thought it can be put in either of them


Welcome, threads merged :)

---

### Post by bodhi.zazen on 2008-11-08
partition magic is a windows application and it often fails at managing Linux partitions.

I suggest you try deleting those partitions and leave the space as unformatted, empty space.

Then try either making a partition with gparted (on the Ubuntu desktop cd), with the Ubuntu installer, or with command line options (fdisk).

---

### Post by Abhishek_12 on 2008-11-08
I tried doing what u suggested still no luck .Here's the screen I'm getting .

---

### Post by bobbob1016 on 2008-11-08
BEFORE starting the install, on the LiveCD, click System -> Administration -> Partition Editor.  Remove everything EXCEPT your XP partition, and click Apply.  Then start the installer, and tell it to use the Free Space.  That should work.

---

### Post by echo.whoami on 2008-11-08
from the live cd open a terminal(applications->accessories->terminal) and write

```
fdisk -l

or

sudo fdisk -l 
```

and post the output

---

### Post by Abhishek_12 on 2008-11-08
> **bobbob1016 said:**
> BEFORE starting the install, on the LiveCD, click System -> Administration -> Partition Editor.  Remove everything EXCEPT your XP partition, and click Apply.  Then start the installer, and tell it to use the Free Space.  That should work.
I did that . It's not showing . It is not able to detect any device which seems quite odd.

I entered sudo fdisk-l in terminal it's not showing anything.

Here's the screenshot . I've even checked the disk for errors .it's not showing any sort of discrepancy

---

### Post by Abhishek_12 on 2008-11-08
Any ideas people its kinda urgent

---

### Post by Abhishek_12 on 2008-11-08
I have tried everything I could found on net still no luck :(

---

### Post by Abhishek_12 on 2008-11-10
Can i get some love :(

---

### Post by torgrot on 2008-11-10
When you tried sudo fdisk -l that is a lower case l not a one.  It should at least show the hard drive.

torgrot

---

