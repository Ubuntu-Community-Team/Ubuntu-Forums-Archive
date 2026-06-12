---
title: "Install 12.04 without disrupting windows"
date: 2012-11-15
forum: New to Ubuntu
---

### Post by L Campbell on 2012-11-15
I have an HP desktop with one hard drive and it is dual boot with WinXP and 11.04.

My goal is to upgrade to 12.04, (since 11.04 is no longer supported) and for which I have downloaded the .iso file, done the md5sum and burned a disk.

My question is what would be the best way to get 12.04 onto my hard drive without disrupting the WinXP system?

TIA.

---

### Post by Pilot6 on 2012-11-15
1. Backup inportant files from Ubuntu partition.
2. Boot from LiveCD
3. Install Ubuntu to the same partition (or partitions) choosing format option.
4. Restore backuped files.

---

### Post by jerome1232 on 2012-11-15
First, backup any data you have, just in case.


If your plan is to just upgrade, I would use an 11.10 alternate cd to upgrade to 11.10 (just stick it in while Ubuntu is running and it should offer to do the upgrade), then once one 11.10, update everything via update manager, then update to 12.04 LTS via update manager. 


It goes without saying that sometimes (they've always worked out for me) upgrades don't work out or have funky problems so keep that 12.04 disc handy.

---

### Post by mlentink on 2012-11-15
Before you go off and format partitions: what's your partition layout? Do you use separate / and /home partitions? If so, at install time you should format **_ONLY_** the root partition, as formatting your home partition will overwrite your data.

---

### Post by Gone fishing on 2012-11-15
Or you could just update to the latest Ubuntu release without uninstalling

[http://www.howtoforge.com/how-to-upgrade-ubuntu-11.10-oneiric-ocelot-to-12.04-lts-precise-pangolin-desktop-and-server](http://www.howtoforge.com/how-to-upgrade-ubuntu-11.10-oneiric-ocelot-to-12.04-lts-precise-pangolin-desktop-and-server)

---

### Post by L Campbell on 2012-11-16
> **jerome1232 said:**
> First, backup any data you have, just in case.


If your plan is to just upgrade, I would use an 11.10 alternate cd to upgrade to 11.10 (just stick it in while Ubuntu is running and it should offer to do the upgrade), then once one 11.10, update everything via update manager, then update to 12.04 LTS via update manager. 


It goes without saying that sometimes (they've always worked out for me) upgrades don't work out or have funky problems so keep that 12.04 disc handy.

Thanks, this was very helpful.

---

### Post by nothingspecial on 2012-11-16
Title changed to reflect the question.

---

### Post by Mr_JMM on 2012-11-16
> **jerome1232 said:**
> If your plan is to just upgrade, I would use an 11.10 alternate cd to upgrade to 11.10 (just stick it in while Ubuntu is running and it should offer to do the upgrade), then once one 11.10, update everything via update manager, then update to 12.04 LTS via update manager.
Would you be kind enough to explain your thinking with this? Why use a DVD to upgrade to 11.10 then update manager to go further? Why not use update manager all the way through (I personally wouldn't as that's a lot of updates / bandwidth) or just use the 12.x DVD go straight from 11.04 as a fresh install?

---

### Post by jerome1232 on 2012-11-16
Becuase 11.04 is End of Life and you'd have to swap your sources to the old releases archives, just seemed easier advise to go with the cd upgrade. Also as I understand it you should go release to release unless your jumping LTS to LTS.

---

### Post by L Campbell on 2012-11-17
> **nothingspecial said:**
> Title changed to reflect the question.

Why did you do this?

What do you mean by it?

---

### Post by jerome1232 on 2012-11-17
Because your original title was horrid (no offense intended), you're lucky anyone actually clicked it to see what's inside.

[http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

That sticky just has tips on getting threads answered, one of the suggestions is this

> Make the title of your thread meaningful and concise. For example, if you are having difficulty using your BroadCom card to connect to your wireless internet, the title "Cannot connect to wireless with BroadCom card" will attract people with experience with wireless internet and BroadCom cards. Titles like "Help me please!!!" or "I have a problem" may be overlooked by people who could otherwise help you.

---

