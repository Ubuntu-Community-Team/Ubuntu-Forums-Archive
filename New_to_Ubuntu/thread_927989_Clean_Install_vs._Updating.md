---
title: "Clean Install vs. Updating"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by PT.Linn.A on 2008-09-23
Looking for a little guidance from the Ubuntu Wizards ... which I am not one of ... YET!  :)

When 8.10 is released, what is the opinion on just doing an update, versus backing up my data and doing a clean install of 8.10?

Opinions (preferably with reasons stated) are appreciated. I want to learn this OS. And, I would like to be able to offer out help to others one day, just as I am receiving help now.

---

### Post by hyper_ch on 2008-09-23
I'm doing a clean install upon each release... normally I use a late alpha version or beta version already...

I do that because I can clean out stuff that I don't need anymore. that's the only reason. I've never tried upgrading.

---

### Post by Tatty on 2008-09-23
I prefer to do a clean install rather than an upgrade.  This just helps to make sure that nothing gets messy in the upgrade.

I maintain a separate /home partition to make this easier.

However since you are saying that you want to learn Ubuntu better than i would recommend doing at least one or two upgrades, just so you can see the process for future reference.

Make sure that you back up any data before doing any sort of upgrade or install to your OS though.

---

### Post by Kain000 on 2008-09-23
Hello and welcome! ):P
When 8.10 is released you will see it as an update.  I'd prefer to just update because it's easier.  but be sure to backup all your data before you do any major update or install (duh) incase you have to revert to your previous setup.  I like the update because assuming that all goes well you will have all your old settings, however you may run into problems with support for the new update as far as your preferences and software go.  I'm not familiar with what is included with this update, if there are alot of redesigned things or it's just a face lift. From what i've read there was a bit of trouble for some people updating form gusty and feisty to hearty, mine went smoothly but there can always be issues.  Just be prepared the the worst and back up.

---

### Post by PT.Linn.A on 2008-09-23
Thanks for the advice and opinion. All have stated clear reason for the advice give, and that is appreciated.

I was leaning towards doing a clean install. However, as pointed out by Tatty, I should do an upgrade or two if I truly want to learn this system.

Good call Tatty!

I am now thinking that I will actually do both.

My intention is to prepare for a clean install (backing everything up and burning a disc.) But, doing an upgrade to see if I can muddle through any difficulties. Then doing a clean install.

Learning/Teaching myself as I go.

---

### Post by hyper_ch on 2008-09-23
Kain000 is partially right about the making of backups before upgrading... however you should regurarly make backups, not only when you intend to do a major change in the system. Hardware can fail at any time ;)

---

### Post by Kain000 on 2008-09-23
> **PT.Linn.A said:**
> 

Learning/Teaching myself as I go.
Thats how I learned!   Ive found that tho Ubuntu /Linux may not be right out of the box functionally that other os's may offer, (i dont mean it doesnt work but for expanded functionality you have to do some tweaking so dont think i'm bashing ubuntu.)  but threw having to edit this text file or tweak that setting i've learned more about linux specifically but computers in general than I would have using windows or mac.
I'm glad to see Ubuntu spreading the "linux word" lol
happy compiling!

---

### Post by PT.Linn.A on 2008-09-23
Yuppers! At one time I thought that I knew computers, but ...


> **Kain000 said:**
> ... but threw having to edit this text file or tweak that setting i've learned more about linux specifically but computers in general than I would have using windows or mac.
I'm glad to see Ubuntu spreading the "linux word" lol
happy compiling!

I now know that the only thing I knew was point and click. Linux is not only functional and powerful, it's an adventure! And, I must say that I am enjoying every minute of it.

The one major issue that I still have though is printer compatibility.

---

### Post by statikeffeck on 2008-10-03
at my home computer I have a fast internet, 2 MB/sec download so updating each ubuntu version isn't really a problem, and it is what I have been doing. 
However, before you do a major version upgrade, your current version must be fully updated -- and doing that requires more downloading and sometimes requires a system reboot. (Actually, on 7.10 I did the updates, didn't want to restart, then invoked the 8.04 Upgrade process. It failed horribly after a while and I couldn't revert or upgrade properly after that, so I HAD to do a clean install. )Depending on how often you do regular updates, this process could take longer than just doing a clean install from an ISO. 

My question is, if we do a new clean install from Ubuntu, can we restore our original environment settings? 
For example, lets say we have a customized system on 7.04, storing all our documents and config files in /home/bobsmith. We back up /home/bobsmith, format, clean install to 8.04. Can we plop back the bobsmith folder, reboot, and have our menus, shortcuts, restored? 
Obviously we will have to re-install any custom packages we installed, but once we do that, will those packages pick up their old settings from the .appgoeshere folders?

---

### Post by philinux on 2008-10-03
I use a separate /home partition so upgrade or reinstall is no problem. My settings are still there.

A reinstall typically takes me 15 minutes then install the extra apps.

---

### Post by wolfen69 on 2008-10-03
> **PT.Linn.A said:**
>  However, as pointed out by Tatty, I should do an upgrade or two if I truly want to learn this system.



what will upgrading teach you? the only thing upgrading will teach you is that upgrades don't always go well. however, this is only my humble opinion. i believe that clean installs are always best. good luck.

---

### Post by ubername on 2008-10-03
> **wolfen69 said:**
> what will upgrading teach you? the only thing upgrading will teach you is that upgrades don't always go well. however, this is only my humble opinion. i believe that clean installs are always best. good luck.

That's a bit like saying that practicing a musical instrument only makes you good at practiciing.

I am all in favour of trying out new things. If you have the disk space, why not try the new distro on a separate partition, or even load the previous version of ubuntu in a separate partition and then try to upgrade?

---

### Post by bhadotia on 2008-10-03
> **wolfen69 said:**
> what will upgrading teach you? the only thing upgrading will teach you is that upgrades don't always go well. however, this is only my humble opinion. i believe that clean installs are always best. good luck.

Why are clean installs always best- you did not give the specific reasons. I'm just curious. 
I have only used two versions of ubuntu and did both upgrade and clean install from gutsy. But in my opinion the upgrade was better 'cause I did not have to waste time on setting up the system.

But if you give good reasons i amy change my opinion.

---

### Post by shifty_powers on 2008-10-03
partly out of pure habit, i keep separate /, /boot, /home partitions so it is easy to do it anyway that i wish :D

---

### Post by jerome1232 on 2008-10-03
If you maintain a seperate /home partition and don't format it when your reinstall then your settings are maintained even if you do a reinstall of the os (I wouldn't actually call this a 'clean' install though for obvious reasons)

Applications settings are maintained in /home/username/.appname folders, the pathing varies a bit between apps.

---

### Post by cariboo on 2008-10-03
Almost all of your program settings are in your home directory, If you are doing a clean installation to a newer version, some of those settings may conflict with the new versions of the programs. I always delete all the configuration files i my home directory, except for ~/.mozilla-thunderbird which is my email directory. I haven't run into any problems so far, but that directory gets backed up every night. I've been using Thunderbird since the second beta release and since then I have accumulated just about 2Gb of email.

Jim

---

### Post by click4851 on 2008-10-03
+1 on the seperate /home partition. Psychocat inspired me to set that up and that makes all the difference in the world. Also makes backups alot easier as well....

---

### Post by wolfen69 on 2008-10-03
> **ubername said:**
> That's a bit like saying that practicing a musical instrument only makes you good at practiciing.



not really a good analogy. 1 of 2 things will happen after an upgrade. 1. everything will go as planned, and there will be peace and harmony in linux land. 2. things will get mucked up and you will have to spend hours trying to fix things that normally would not go bad. and the problems that might occur after an upgrade are not necessarily going to be "normal" problems, and will only serve to teach how to fix an upgrade gone bad. if you do not do an upgrade, you do not have to learn how to fix problems associated with it. i prefer to avoid problems in the first place. hence, the clean install.

everyone has a different opinion about this and it is not worth arguing about. if you decide to go with upgrading, good luck to you. you have been warned.

---

