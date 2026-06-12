---
title: "upgrade versus clean install"
date: 2013-05-12
forum: New to Ubuntu
---

### Post by teacherjeff on 2013-05-12
Ever since I've been involved with computers (close to 30 years now), I've had a strong prejudice against "upgrade" or "update" options for software, espeically operating systems. I have always leaned very much toward doing a clean install. Some of this prejudice may come from Windows upgrades years ago, which IIRC sometimes left you with a system that was neither all-old nor all-new. And whenever something goes wrong, you always wonder if it had to do with the upgrade somehow.

Now that Ubuntu 13.04 is out, I'm thinking maybe I'll reconsider and go the upgrade route. I don't have a huge amount of software and data installed, but upgrading would save me from quite a bit of tweaking to get everything set again the way I like it.

What say you? Upgrade or clean install?

---

### Post by fantab on 2013-05-12
I always do a clean install. I like tweaking, so I find it fun to set it up all again. It is fresh and clean every time. But that's me. ;)

I set up my computer for a clean install. I have all my data on a separate Data ext4 partition. So I don't have to worry about data loss. Just 25GB '/' partition. Wipe it clean and install. I have on another 25GB partition with '/' 12.04LTS. This partition always keeps the latest LTS version.

I am currently using "Saucy Salamander" 13.10 Development.

Regards..

---

### Post by ibjsb4 on 2013-05-12
Are you running 12.10?  Then sure, go for it.  If it doesn't work (and it probably will) you were considering a fresh install anyhow :)

Are you coming from something old? Like maybe 10o4?  Then I say a fresh install.  An old release like 10o4 is gnome2 and I think better to get it all fresh gnome3, but then again, people do it with success.

---

### Post by oldfred on 2013-05-12
I am like fantab, I prefer clean installs. And have data in separate data partitions. I install new versions and beta enough times that I found myself doing some of the same configurations and now have scripted some of the changes I want.

But I cheat. Since I only use 25GB for / (root) I just install in a new 25GB partition. Then if new install does not work or has issues I still have my old install. And I can go back and figure out some setting I forgot that I really liked.

Since my wife complained about too many upgrades, I now use 12.04 as my working install, but still install every new version in at least one new / partition to test.

---

### Post by deadflowr on 2013-05-12
Seeing as to it that you do fresh installs, I would assume you have backups.

What you could do, as to try upgrading, would be to first download the ISO for insurance purposes.
Then run the upgrader, and see if things bork up or not.

If it goes bad, then at least you've got an install disk you can run.

Worse case, the ISO is bad, and the upgrade fails, you'll have to load an older version and try again.

Personally, I've been very fortunate with the upgrade method.
Others have not.

---

### Post by Impavidus on 2013-05-12
Some people will tell you their upgrades never work. Other people will tell you their upgrades always work. That's the group I belong to. Few people will even tell you it sometimes works and sometimes not, but it seems to fail reliably: if it works once for someone, it works the next time too, if it fails, it always fails. Slightly exaggerating.

It seems te depend on things like PPAs, proprietary drivers and manual system tweaks. The closer your system is to one that only has software from the repositories, the less likely you get into trouble. Also, going the "official" way, from one release to the next or from one LTS release to the next LST release, is more reliable than editing the software sources and taking shortcuts.

---

### Post by Frogs Hair on 2013-05-12
I notice upgrades are very slow slow to unpack and set up after watching a friend's upgrade . Be patient and don't run applications during the process. I prefer clean installations which are much faster.

---

### Post by teacherjeff on 2013-05-13
Thanks for the replies. I'll give the upgrade a try. As several people have pointed out, if it doesn't work I won't really have lost anything.

---

### Post by pfeiffep on 2013-05-13
> **teacherjeff said:**
> Thanks for the replies. I'll give the upgrade a try. As several people have pointed out, if it doesn't work I won't really have lost anything.
My upgrade from 12.10 to 13.04 was extremely slow.

---

### Post by ibjsb4 on 2013-05-13
Don't forget :)

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by Mark Phelps on 2013-05-13
Every upgrade will have some changes -- and when things are removed or support is dropped for older versions, the upgrades go badly. And, because there is no "roll-back" option to restore the previous working version, when they do go badly, you can have a lot of work ahead of you to fix the problems.

Myself, I always do clean installs because of this.

---

### Post by craig10x on 2013-05-13
> **teacherjeff said:**
> Thanks for the replies. I'll give the upgrade a try. As several people have pointed out, if it doesn't work I won't really have lost anything.

Exactly, worse case scenario...you end up re-installing which you were going to do anyway...;)

I've never done an upgrade, but plan on trying one on my 13.04 install when 13.10 goes final...I have always heard that it's best to do the upgrade during the first few weeks when the new version goes final, so i plan on doing just that...if it can save me the bother of re-installing, that would be great...i have all my important data saved on a flash drive, but it's a bit of a routine to have to add it back in every time on a fresh install...i figure that if i don't get a successful upgrade, then just wipe it clean and do a fresh one, so nothing to lose by trying (and keeping the fingers crossed...LOL)....

---

### Post by BikeRich on 2013-05-13
teacherjeff :

     The upgrades I've done were VERY slow, and not always satisfactory.  Now I always do a fresh install on partition "/" .  All the stuff on partition "/home" is still there, including a brief list of the apps I lost

because of the fresh install.  And of course there is the "swap" partition also.

                                                              bikerich

---

### Post by pfeiffep on 2013-05-13
Since I have a tripple boot system one of which is Win 7 I use and external esata hard drive for data storage ... this provides me with the comfort that an install won't touch my documents!

---

### Post by craig10x on 2013-05-13
After you do the upgrade, i think it would be interesting for you to report back here on your results...

---

### Post by DuckHook on 2013-05-13
> **Impavidus said:**
> Some people will tell you their upgrades never work. Other people will tell you their upgrades always work. That's the group I belong to. Few people will even tell you it sometimes works and sometimes not, but it seems to fail reliably: if it works once for someone, it works the next time too, if it fails, it always fails. Slightly exaggerating.

:lolflag:

This variation of Murphy's law is hereby dubbed Impavidus' Law.

Exaggeration is the spice of life.

---

