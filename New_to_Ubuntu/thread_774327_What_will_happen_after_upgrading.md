---
title: "What will happen after upgrading?"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by sayakb on 2008-04-29
I am planning to upgrade to Hardy. But I have many apps installed which I downloaded from getdeb.net and linux.softpedia.com. What would happen to those as they wouldn't be updated naturally. Will they be automatically removed or would they make my critical libraries to break, or will I have to somehow add getdeb to my repos?

---

### Post by Anduu on 2008-04-29
Most of the time your apps should be ok.

If dependency problems with some apps are encountered during the upgrade process they will be removed however you settings etc for that app will be retained so if you find an updated version you should be good to go.

You may also find that newer versions of some apps(particularly those from GetDeb...)may be available in Hardys repos.

Things installed from source may need to be recompiled/installed.

I have upgraded many times and never run into any serious issues with third party apps.

---

### Post by sayakb on 2008-04-30
That sounds good enough :)
Thanks for replying

---

### Post by fhmanas on 2008-04-30
My suggestions is don't go the upgrade route.  I did it and it was not pretty.  The upgrade had problems especially with the apps installed.  The end result was a sluggish machine that forced me to just start with a fresh install.  Even at that, the results were not astounding.  If your system is ok, and there is no great need to upgrade except curiosity, then don't.  Anyway, you can test out Hardy in a virtual machine.

---

### Post by sayakb on 2008-05-01
> **fhmanas said:**
> My suggestions is don't go the upgrade route. I did it and it was not pretty. The upgrade had problems especially with the apps installed. The end result was a sluggish machine that forced me to just start with a fresh install. Even at that, the results were not astounding. If your system is ok, and there is no great need to upgrade except curiosity, then don't. Anyway, you can test out Hardy in a virtual machine.
So should I backup my data instead and go for a clean install rather than upgrading?

---

### Post by Paqman on 2008-05-01
> **LinuxIsInnovation said:**
> So should I backup my data instead and go for a clean install rather than upgrading?

Depends. It's mostly just a matter of personal preference. Somebody who's had an upgrade go badly is likely to tell you do a fresh install, while someone who's had several upgrades work perfectly is likely to tell you the opposite.

Depending on how fast your internet connection and PC are, and how au fait you are with reinstalling it can sometimes be quicker to reinstall than to upgrade.

Personally i'd say take a crack at the upgrade. If anything breaks, you can always do the fresh install. If not, happy days!

Either way, back up your data. It's a good thing to do even if you aren't messing with your system.

---

### Post by sayakb on 2008-05-01
Even if something breaks, I think I could access my HDD thru the liveCD and recover my data, can't I? Since it is a lot of data and I don't seem to have any means to back it up :(

---

### Post by Cadmus on 2008-05-01
I don't think there's any risk of an upgrade rendering a drive unreadable or utterly trashing your files, so you're right, if things do go wrong you can always pull stuff off with a LiveCD or a Knoppix disc.

---

### Post by Paqman on 2008-05-01
> **LinuxIsInnovation said:**
> Even if something breaks, I think I could access my HDD thru the liveCD and recover my data, can't I? Since it is a lot of data and I don't seem to have any means to back it up :(

Probably. The kind of things people report as breaking tend to be minor things.

There is a couple of ways you could back up data. Create a separate partition using Gparted and copy your data over there. If you include your /home folder, your /etc/fstab, and a [list of all your installed packages](http://ubuntuforums.org/showthread.php?t=261366) then it'd make a pretty handy reinstallation kit. Handy thing to have tucked away.

Or you could back up to some online storage. It's slow but has the advantage of being immune to anything that goes wrong with your machine.

---

### Post by sayakb on 2008-05-01
Okay, I would go for upgrade then :)
Thanks for replying

---

### Post by Toasted Donut on 2008-05-01
I upgraded. I got to keep all my files but I had to wait a hour and a half just to download the update :( . Also I was left unhappy with a mesh of Gutsy-Hardy stuff leftover from the update, so I just did a clean install, it's a lot less complicated. Note: you should backup your files before doing a clean install :) As and added bonus you have a newer LiveCD too.

---

### Post by sayakb on 2008-05-03
I have ordered a CD on shipit, though I would first upgrade, and then go for a clean install if something goes wrong perhaps..

---

