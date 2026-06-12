---
title: "[SOLVED] Running Ubuntu 7.10, should i upgrade to 8.04?"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by aMadMan on 2008-08-01
So i am currently running 7.10 as the title says.

I noticed that 8.04 is out, but that it is an LTS version.  should i upgrade to 8.04 even tho it is LTS? actually, what im really wanting to know is, when the next version of ubuntu comes out (which wont be LTS) will i be able to upgrade to that from the 8.04 LTS version?

Any suggestions would be greatly appreciated.

---

### Post by dca on 2008-08-01
LTS = long term support.  You get updates on desktop 8.04 vers for three years and five on server.
 
7.10 = 18mos support/updates on server/desktop vers.
 
I don't use the upgrade, I copy all data from /home and do clean installs.  Many people have had great success doing upgrade, but me, heck, the upgrade doesn't work in Windows, why should it work in Linux.  I know, crappy attitude, I have the same ideology when it comes to servers as well...

---

### Post by aMadMan on 2008-08-01
> **dca said:**
> LTS = long term support.  You get updates on desktop 8.04 vers for three years and five on server.
 
7.10 = 18mos support/updates on server/desktop vers.
 
I don't use the upgrade, I copy all data from /home and do clean installs.  Many people have had great success doing upgrade, but me, heck, the upgrade doesn't work in Windows, why should it work in Linux.  I know, crappy attitude, I have the same ideology when it comes to servers as well...

Hrmm, i agree with your logic.  i keep my home folder files mounted from a samba share anyways, so a fresh install should be a breeze anyways.  I guess i'll see what everyone else says (assuming anyone else responds) and go from there.

---

### Post by Aetherius on 2008-08-01
I've heard good things about the upgrade this time around but my advice....

1) backup everything you need to keep

2) reinstall your new version, but make a separate partition and mount it as /home

3) then next time you want to upgrade you can just reinstall over the old ubuntu and keep all you /home files perfectly intact

sorry if this is a bit much for the absolute beginner section :lolflag: but i can knock up step by step howto if anyone wants (on second thoughts theres probably one already around this forum somewhere :P )

---Aeth

---

### Post by decoherence on 2008-08-01
Some people are experiencing hard lockups with Hardy. Some people say linux 2.6.18 was the last reliable version. I can't really comment on that since I haven't had many problems and nobody has a clear idea of what the cause(s) is/are.

I had a hard lockup once after upgrading to Hardy but it's been smooth sailing since. Hopefully I haven't jinxed you by mentioning it! ;)

And yes, you will be able to upgrade whenever you like, if upgrading is what you want to do. dca's method is a good one too and not much more complicated than an upgrade. (way simpler, actually, if the upgrade doesn't work! they usually do tho)

---

### Post by ARhere on 2008-08-01
> **aMadMan said:**
> ...what im really wanting to know is, when the next version of ubuntu comes out (which wont be LTS) will i be able to upgrade to that from the 8.04 LTS version?...

I cannot imagine why not.  I personally like 8.04 more then 7.10, but it is up to you.

> I don't use the upgrade, I copy all data from /home and do clean installs. Many people have had great success doing upgrade, but me, heck, the upgrade doesn't work in Windows, why should it work in Linux.

Hate to say it, but I agree.  When moving to new versions of Windows or Linux I _always_ installed fresh leaving "My Documents" or "/home" on a separate drive.  Not saying the Upgrade does not work, but it never seems to work right for me.

-AR

---

### Post by unutbu on 2008-08-01
If you shrink your Ubuntu 7.10 partition by 10GB, you can create a new partition for 8.04. You could then do a manual (rather than "guided") install of 8.04, where you direct it to install into the new partition.
If you do it this way, you never have to scrap your working OS before trying the new OS.

Since you have /home already on a different partition, you can set up 8.04 to mount that /home partition too, so you can have two Ubuntus both using the same /home accounts.

There can be some problems sharing /home accounts, however, so to really do it right, share a /data partition (the samba partition), and let each OS have its own separate /home. (See [http://ubuntuforums.org/showpost.php?p=5465718&postcount=2](http://ubuntuforums.org/showpost.php?p=5465718&postcount=2))

---

### Post by Paqman on 2008-08-01
Sure, why not? The new version will include newer versions of all your software.

Back up your data before doing either an upgrade or reinstall. If you have your /home on a seperate partition then that's all sorted, if not then back that up too.

If you decide to resintall you can [automate the reinstallation of all your software](http://ubuntuforums.org/showthread.php?t=261366).

---

### Post by mjitkop on 2008-08-01
Hi, aMadMan.

As the saying goes: "if it ain't broke, don't fix it"

What I mean is that if you are not having any problems with 7.10 and are happy with it then why upgrade? Is there anything that you would get or would be able to do with 8.04 that you are missing in 7.10?

It's just up to you to decide if you really need to upgrade. Technically speaking, there is nothing seriously dangerous with running 7.10 so there are no reasons that you should upgrade to 8.04. ;)

---

### Post by Thelasko on 2008-08-01
What kind of computer is it?  The only problems I have heard about with Hardy involve HP laptops.  Everything else should be fine.  I would say my Dell runs much better on Hardy than it ever did with Gusty.

---

### Post by dca on 2008-08-01
What makes me leery are the changes made in GNOME, gvfs, etc, etc from Ubuntu 7.x to 8.x...  A lot of your custom settings, possible themes, app profiles created when certain software is run for the first time all get stored as '.' hidden files in your /home/username directory.  It's safer to just couple all your personal data onto another drive or optical disk and do a fresh install....

---

### Post by aMadMan on 2008-08-01
> **dca said:**
> What makes me leery are the changes made in GNOME, gvfs, etc, etc from Ubuntu 7.x to 8.x...  A lot of your custom settings, possible themes, app profiles created when certain software is run for the first time all get stored as '.' hidden files in your /home/username directory.  It's safer to just couple all your personal data onto another drive or optical disk and do a fresh install....

I am thinking thats the route i may go, gives me an excuse to re-setup things a bit more cleanly. thanks!

---

