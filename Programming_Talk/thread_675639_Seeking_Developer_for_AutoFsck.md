---
title: "Seeking Developer for AutoFsck"
date: 2008-01-22
forum: Programming Talk
---

### Post by musther on 2008-01-22
I'm the developer of AutoFsck, it's a tool to make running fsck much more user friendly in Ubuntu, see here:
[https://wiki.ubuntu.com/AutoFsck](https://wiki.ubuntu.com/AutoFsck)
Blueprint:
[https://blueprints.launchpad.net/ubuntu/+spec/prompt-for-fsck-on-shutdown](https://blueprints.launchpad.net/ubuntu/+spec/prompt-for-fsck-on-shutdown)

AutoFsck provides functionality which, according to the user base, should have been included in Ubuntu a long time ago.  

The current incarnation is a bash script, which leaves a little to be desired, and probably isn't really ready to be included in a release - but nevertheless, the functionality should be.

So I'm seeking a developer, preferably somebody with some experience at writing code for inclusion in the distribution, to help me get AutoFsck up to scratch for inclusion.  The users want it, we just need to get it done.

Thanks, and I hope you will seriously consider helping.

---

### Post by Birk on 2008-01-25
Hi,
I am by no means a developer and can't help you with this (sorry).
I just think that this is very important and totally agree, 
A fix to fsck is absolutely needed! 
I just can't imagine trying to give a presentation e.g. and having to wait for my system to boot for ever. This would be absolutely embarrassing for me and for ubuntu as well (out in the public)!

Thanks for the good start Musther
Birk

---

### Post by vnkatesh on 2008-01-26
I've got no influence/previous experience in writing code for actual distribution purposes.. But still willing to help you in any method of code development.

---

### Post by cesium62 on 2008-01-26
While running fsck at shutdown or at a time that is convenient to me instead of at a random startup is really nice, this doesn't fully solve the problem.  The problem is that I don't want my computer tied up for 20 minues while fsck is running.  fsck was invented back in the day before journaled file systems.  Now that we have journaled file systems, the utility of fsck is greatly diminished.

How about a read-only mode of fsck that can be run in the background to check for problems on the disk?  If no problems are found, update the counter.  If problems are found, crash the system and run the 20 minute fsck on a writeable disk.

Are you worried that writes to the disk will interfere with the read-only fsck?  Build a data logging area where writes can be posted for later flushing to the correct location.  If the area fills up, stop the fsck, flush the logging area, and restart the fsck later when the system looks idle.

---

### Post by Vadi on 2008-01-26
I don't think re-coding fsck is the scope here. AutoFsck's goals are good enough for most of us, and I'd gladly see it included by default. Until then, it'll be one of the first programs I install on a new Ubutnu.

---

### Post by musther on 2008-01-26
Rewriting fsck was not part of the plan, but cesium62's idea would the the ultimate way to solve the problem.  For now, as meg23 said herehttp://ubuntuforums.org/showthread.php?p=4211101#post4211101
we need to define "a state which is appropriate for inclusion in Ubuntu".  For example I know it needs to be translatable to languages other than English, I'm not sure how Ubuntu does this and how we'll have to do it.

---

### Post by Birk on 2008-01-26
If there is need, I am a native german speaker and could translate it to german.
(My english is halfway OK, since I am living in the states for a couple of years now)
Birk

---

### Post by jlebrech on 2009-03-14
I could translate It to French for you.

---

### Post by slavik on 2009-03-14
have you tried talking to the MOTU team?

---

