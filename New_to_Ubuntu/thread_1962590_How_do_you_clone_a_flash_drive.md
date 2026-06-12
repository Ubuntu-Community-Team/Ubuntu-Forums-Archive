---
title: "How do you clone a flash drive?"
date: 2012-04-21
forum: New to Ubuntu
---

### Post by Boyntonstu on 2012-04-21
I have 11.10 running pretty well.

My transition to Ubuntu began when my wife's 2.8 Ghz P4 XP machine began to go blue.

CCleaner helped somewhat, but this PC has apparently accepted some uninvited guests over the years.  AAMOF we could never update it to SP3.

Necessity being the mother of invention, and learning to dislike Windows, I installed 11.10 on a flash drive as an alternative OS.

For the last 2 weeks I have been running 11.10 with fast and reliable performance.

I am ready to clone my flash drive and my Plop USB boot disk.

What method do you suggest for USB flash cloning?

---

### Post by JC Cheloven on 2012-04-21
Hi, I'm addmitedly a bit confused about your question. To simply answer I'd suggest you to use the dd comand. Please run
```
man dd
``` for further details.
But I actually think that you intend to do something a bit different, like installing ubuntu in your hard disk, to replace xp, or alongside it. If this is true, you should have in the live session (from your pendrive) an icon to install... could you please clarify what your final intent is?

---

### Post by MartyBuntu on 2012-04-21
> **Boyntonstu said:**
> 
Necessity being the mother of invention, and learning to dislike Windows,


> **Boyntonstu said:**
> 
For the last 2 weeks I have been running 11.10 with fast and reliable performance.


Seems like the oppurtunity for a brand new, full hard drive install of Ubuntu, don't you think?

---

### Post by Boyntonstu on 2012-04-21
> **MartyBuntu said:**
> Seems like the oppurtunity for a brand new, full hard drive install of Ubuntu, don't you think?

I agree that a full install is the last step.

But first, she needs to get used to Ubuntu.

A weekly blue screen is not nice, but she can live with it for a little bit longer.

BTW After you have customized a version of Ubuntu to your satisfaction, it seems that a version update would keep the features.  OTOH  a fresh install would require you to do it all over again.

I like Firefox updates because the add-ons that do not work are grayed out.  When compatible add-ons become available, a click installs them.


It would be great if the features/mods of Ubuntu could be saved and re-installed (if they work) with the newest version.

---

### Post by JC Cheloven on 2012-04-21
> **Boyntonstu said:**
> For the last 2 weeks I have been running 11.10 with fast and reliable performance.
You may be overcomplicating things. Any customization you did in these two weeks can be typically re-done in no time, and it's safer than porting sparse configuration files. My advice (after installing for a 100+ people) would be to keep your documents in a safe place, and go for a fresh install.

If your wife still needs windows, do a dual boot. Works nicely ;)

Cheers
JC

---

### Post by Boyntonstu on 2012-04-21
> **JC Cheloven said:**
> You may be overcomplicating things. Any customization you did in these two weeks can be typically re-done in no time, and it's safer than porting sparse configuration files. My advice (after installing for a 100+ people) would be to keep your documents in a safe place, and go for a fresh install.

If your wife still needs windows, do a dual boot. Works nicely ;)

Cheers
JC

Point, well taken.

How long to wait before version 12 'matures'?

---

### Post by jerrrys on 2012-04-21
> **Boyntonstu said:**
> Point, well taken.

How long to wait before version 12 'matures'?

Its an LTS Release, you can do a release upgrade in a few days when the stable release comes out.

In terminal:

sudo do-release-upgrade -d

Upgrade to 12o4 has worked well for me.

---

### Post by JC Cheloven on 2012-04-22
> **Boyntonstu said:**
> Point, well taken.
How long to wait before version 12 'matures'?

I'd say, from previous experience, that 1-2 months is reasonable. In this time the developers usually get ironed out some possible rough edges.

On the other hand: be prepared to see in the forums a lot of complaints and problem reports. Don't get fooled, keep in mind that only people having problems will post, but this people isn't a majority at all in the big numbers (well, it was like this so far). It happened specially in the past with LTS releases. I still remember the 'massive' (apparently) rants about 8.04 Hardy Heron when it came out, and almost the same for 10.04 Lucid Lynx. But in the long run, they have beeen good LTS versions. No doubt that the forthcoming 12.04 Precise Pangolin will be 'greeted' in a similar way. 

Cheers
JC
____________

---

