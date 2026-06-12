---
title: "Flash videos quit working"
date: 2012-08-07
forum: New to Ubuntu
---

### Post by Autodave on 2012-08-07
2 machines running Xubuntu 12.04 and one new conversion to 12.04: no you tube videos working.  (On the 2 machines that were already running Xubuntu, it worked fine until a few days ago.)  I have tried re-installing Flash and Gnash to no avail.  The restricted extras and add-ons are installed.  VLC and all Gstreamer add-ons installed.

Any ideas?  I am used to fighting with Flash, but it has me stumped this time.

---

### Post by Autodave on 2012-08-12
> **Autodave said:**
> 2 machines running Xubuntu 12.04 and one new conversion to 12.04: no you tube videos working.  (On the 2 machines that were already running Xubuntu, it worked fine until a few days ago.)  I have tried re-installing Flash and Gnash to no avail.  The restricted extras and add-ons are installed.  VLC and all Gstreamer add-ons installed.

Any ideas?  I am used to fighting with Flash, but it has me stumped this time.

I sort of have an answer to my own question.  I had given up trying to solve the problem and only today have a partial answer.  I am posting this in hopes of saving some one else from going prematurely insane.

As I said before, all machines running Xubuntu 12.04 AND able to watch Youtube videos on them.  For no reason that I could find, 2 machines quit having the ability to show Youtube.  I need to say that both of these machines were old: a 533Mhz and a 1,000Mhz.  Both with 1/2 gig ram.  Neither had proprietary video drivers: none were available.

A friend came over with a Windoze machine that had quit working.  Preliminary inspection indicated it had a bad hard drive.  However, I did not have a spare PATA drive to try.  So, I pulled one out of one of my machines that was running Xubuntu 12.04: one that would NOT play Youtube videos.  I put that drive into his machine and booted it up.  After Xubuntu did its reconfiguration for about 15 seconds, the machine booted to the desktop.  EVERYTHING worked including Youtube videos.  No proprietary drivers were installed!

I am guessing that a previous kernel update is what took out the Youtube videos and I am also guessing that the old motherboards / processors were affected by that upgrade.

Anyway, removed the HD from his machine and put back into mine: you guessed it: no Youtube videos.

I will close this thread now.  Like I said, I really don't have an answer, but it has to be something with the kernel update and the age of the machines it affected.

---

