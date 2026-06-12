---
title: "New Releases"
date: 2011-09-15
forum: Recurring Discussions
---

### Post by Gwaro on 2011-09-15
I would like to know which way is better to get the new releases:new installation or upgrade?

---

### Post by haqking on 2011-09-15
> **Gwaro said:**
> I would like to know which way is better to get the new releases:new installation or upgrade?


The best way IMO is to do a fresh install, just make sure you have a complete backup of data.

Also make sure you try the new version out first either with Live CD/DVD or USB or possibly a dual boot etc.

Either way try before you buy as it were ;-)

So many people complain about not liking something new in the upgrade....well dont upgrade then...simple ;-)

peace and enjoy

---

### Post by drs305 on 2011-09-15
This topic is brought up with each release and is frequently discussed at length.

There are opinions on both sides. It may depend on how much customization you wish to retain from your current installation. Various Ubuntu packages allow you to export settings which you may be able to use in a clean installation, and having a separate /home also helps with retaining user settings.

Here is an example of a previous thread:
[http://ubuntuforums.org/showthread.php?t=1462619&highlight=upgrade+clean]("http://ubuntuforums.org/showthread.php?t=1462619&highlight=upgrade+clean")

---

### Post by Gwaro on 2011-09-15
> **haqking said:**
> The best way IMO is to do a fresh install, just make sure you have a complete backup of data.

Also make sure you try the new version out first either with Live CD/DVD or USB or possibly a dual boot etc.

Either way try before you buy as it were ;-)

So many people complain about not liking something new in the upgrade....well dont upgrade then...simple ;-)

peace and enjoy



Thanks for your info. However i would like to know further  how to backup my data and if i will need to install afresh all  the applications i have.

---

### Post by haqking on 2011-09-15
> **Gwaro said:**
> Thanks for your info. However i would like to know further  how to backup my data and if i will need to install afresh all  the applications i have.


see the link drs305 posted above me as it covers most of that. and here for [BackingUp]("https://help.ubuntu.com/community/BackupYourSystem")

---

### Post by 3rdalbum on 2011-09-15
> **Gwaro said:**
> if i will need to install afresh all  the applications i have.

It depends how you do it. If you erase the partition, then yes you will lose your data and have to manually reinstall your programs.

If you use the "Something else" function in the Ubuntu installer to manually select a partition to install to, and you DON'T opt to format the partition, it will preserve the /home directory and make a note of what programs you have installed. Then at the end of the installation it will download new versions and reinstall those programs for you.

If you do an in-place upgrade using Update Manager, you won't lose data. I just successfully upgraded from 11.04 to 11.10 beta, so I can testify that the process does work. I hadn't done anything outrageous to my system, though; some people do and then come into trouble.

---

### Post by drs305 on 2011-09-15
I'll add one more observation. If you make a backup of your existing installation via rsync, fsarchiver, etc, you can always try the online upgrade. If it doesn't work, you can revert to the old installation or do a clean one. 

I've done online upgrades without problems many times, but you never can be sure if it will work out or not.

---

### Post by snowpine on 2011-09-15
Some users prefer a fresh reinstall every 6 months. Other users (including myself) have good luck upgrading.

Upgrading is recommended and fully supported by Ubuntu, see here: [https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

ps Having a good backup policy is just common sense, regardless of whether you choose to upgrade or fresh reinstall.

---

