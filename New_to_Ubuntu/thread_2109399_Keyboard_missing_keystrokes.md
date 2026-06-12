---
title: "Keyboard missing keystrokes"
date: 2013-01-27
forum: New to Ubuntu
---

### Post by cstambaugh on 2013-01-27
Hello all
I have Ubuntu 10.04 on my laptop, and am using WINE to run Microsoft office 07. All of a sudden recently my keyboard misses strokes in using Microsoft office. I tried re installing WINE and Microsoft office, but it still occurs. This is the only program it does it in (so far) that I have noticed. It does not matter if I plug in a USB keyboard or not. It has not done anything as of yet making this post. I dont know where to look to try and cure this as it seems to be localized in the one program, for now, but a re install did not cure the issue. Does anyone have any clues or have had this issue before and can point me where to look?
Thanks

---

### Post by TheFu on 2013-01-27
I do not know the answer.  First, what do the log files show?  Look in /var/log/*

Is it possible that your locale isn't the same between WINE and Ubuntu?  I don't know what effect this will have, if any, just brainstorming.

It might be helpful to know exactly which version of MS-office you are running and which other programs you run under WINE that **do not** show the same issue. It won't help me, but maybe someone else?  The exact version of WINE and any WineTricks would be good to know too. Any WINE overrides?

Next, you do realize that 10.04 desktop support ends in 2 months and will not get patches. I know that it hasn't gotten Firefox/Thunderbird updates (at least from the Mozilla PPA) for months. 
12.04 is fine and if you don't like Unity, there are lots of other options easily installed. With 12.04 as an LTS release and a change in Canonical support times, this desktop will have 5 yrs of support, not the 3 that 10.04 got. 

Can you please confirm that this is a WINE-only issue?  If so, perhaps changing the title of this thread to include WINE would be helpful so this thread will be moved to the WINE support forum where people with more expertise hang out?

---

### Post by cstambaugh on 2013-01-27
Thanks for the reply. I changed the OP to reflect that it was in WINE and in Office 07. I cannot find anything in the logs, there are so many there in that folder and Ive looked at them all and could not find an answer.
I did not know about the support ending for this version I finally got this one set up how I like and with the options I like and am Familiar with.. 
I did try the latest once, but I did not like the desktop interface as much, but maybe Ill look into a different one. Maybe when my classes are over this term, and I have a break ill try swapping it and finding another desktop option.

---

### Post by TheFu on 2013-01-27
> **cstambaugh said:**
> Thanks for the reply. I changed the OP to reflect that it was in WINE and in Office 07. I cannot find anything in the logs, there are so many there in that folder and Ive looked at them all and could not find an answer.
I did not know about the support ending for this version I finally got this one set up how I like and with the options I like and am Familiar with.. 
I did try the latest once, but I did not like the desktop interface as much, but maybe Ill look into a different one. Maybe when my classes are over this term, and I have a break ill try swapping it and finding another desktop option.

This should help:
$ sudo egrep -i 'warning|error' /var/log/* | more

I would strongly suggest that you not wait to update. Not being on a currently patched OS - any OS - is dangerous. There are known issues.

Installing and using in a new DE (Desktop environment) is as easy as installing any other program on Linux, then selecting them at the login screen (the little cog next to the login name has a selection). You don't even need to remove Unity if you don't want too.  Having 10+ choices at login can be fun. It is just disk space.

Of course, before doing any OS update, we all need a full backup.  

I think going from 10.04 to 12.04 took about an hour on Mom's PC last fall. It was painless. I even did it over the internet, the day before I would be in her city.  At login, you should see the** do-release-upgrade** prompt.  She was running Lubuntu and stayed with that release.  It has a much simpler GUI, not Unity.  XFCE or Cinnamon are other non-Unity options good for non-experts.

This explains how to load Cinnamon on 12.04 desktops:
[http://askubuntu.com/questions/94201/how-do-i-install-the-cinnamon-desktop](http://askubuntu.com/questions/94201/how-do-i-install-the-cinnamon-desktop)
Easy-peasy.

Plus, if you are on a supported release, people here are more likely to be able to help you with issues.

With you being on an old release, that tells me that you should not load 12.10. Stay with 12.04, the LTS version.

Sorry I can't help with the dropped keyboard issue. Hopefully the logs will show a failing keyboard or some other issue.

---

