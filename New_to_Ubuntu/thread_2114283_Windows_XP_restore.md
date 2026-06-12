---
title: "Windows XP restore"
date: 2013-02-09
forum: New to Ubuntu
---

### Post by hintzer on 2013-02-09
My parents home computer was running Windows xp on it but it became corrupt and now shows the blue screen of death after it starts, I have tried using the re install disk that was provided when the computer was bought but had no luck either. I have now got a bootable kubuntu os flash drive and was able to boot the computer into kubuntu. My goal is to try and format the hard drive and resinstall windows xp, is that possible to do from kubuntu if i still have the windows xp reinstall cd?

---

### Post by Mark Phelps on 2013-02-09
Linux provides no way to install a Windows OS -- but, if you repartition a drive, that can prevent Recovery tools from working in Windows because, sometimes, they expect to see the original partitioning scheme on the drive and fail if they don't.

IF you want, you could boot from a Linux CD and use GParted on that to remove the partitions on the PC, at least that way, when you boot from the XP CD, it won't find partitions that it doesn't understand.

But, BEFORE you do this, you need to be sure that what you have is a full XP Installation CD, not just a Recovery CD.  The former includes all the files needed to install Windows, the latter just includes a utility that will restore Windows from a Recovery partition on the drive -- and if that partition gets damaged, or moved, or resized, or (in some cases) if you have OTHER partitions on the drive, the Recovery CD often will not work.

---

### Post by hintzer on 2013-02-09
Is it possible to run a system restore from kubuntu?

---

### Post by MadmanRB on 2013-02-09
> **hintzer said:**
> Is it possible to run a system restore from kubuntu?

Nope, only an XP disk can do that.
Do yourself a favor and dual boot, XP is going to be non supported soon so better start getting used to linux or get a new computer with windows 7 installed.

---

### Post by wejones10 on 2013-02-09
You can download HIRENS CD.  This is a bootable xp cd with a number of tools that can help you restore your xp.

Have you tried booting into safe mode, press F5 while booting and select safe mode?

---

### Post by DuckHook on 2013-02-09
Basically, XP will no longer be supported by MS beyond April 8 2014. While that's more than a year away, it makes good sense to start prepping now. Much of the HW that worked tolerably well with XP is now too underpowered for W7 or even Ubuntu for that matter. So your choice of Xubuntu (even if just for recovery) was a good one.

@MadmanRB is absolutely right... you do not want to be caught with an unsupported XP. The OS is so insecure that it is a big fat target for crackers and script kiddies, and once updates stop, it is a recipe for getting owned. This is all the riskier for the type of users "parents" tend to be, because when it comes to OSes, most older users don't know their knees from their elbows--and this is coming from a man who is both retired and a grandpa. In fact, I have been predicting for a long time that the end of support for XP will see yet another meteoric rise in the number of computers that get keylogged, become spambots, or screw their users through password and identity theft, because most of these users will greet the disappearance of updates and/or virus measures as a perverse benefit, in that they no longer have to put up with them.

This is the ideal time to dual boot. If you have to rebuild their OS anyway, then take the little additional time to partition properly and install Xubuntu. You should also consider Lubuntu. Stay away from Ubuntu, because, even if their HW is powerful enough to run it, it differs too much from XP for your parents to get used to. Install apps as similar as possible to what they are used to, try WINE for Win apps they insist on, and slowly condition them to K/Lubuntu over the next year. This is the strategy I employ with my friends and family, and it works very well because it's a go-at-your-own-pace approach that doesn't spook older people (we like to handle things at *our* pace, not *yours*).

---

