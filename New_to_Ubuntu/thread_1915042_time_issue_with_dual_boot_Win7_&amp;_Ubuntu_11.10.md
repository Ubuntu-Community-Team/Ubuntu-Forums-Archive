---
title: "time issue with dual boot Win7 &amp; Ubuntu 11.10"
date: 2012-01-25
forum: New to Ubuntu
---

### Post by bpb_21 on 2012-01-25
I've got an issue, and I know the answer is out there somewhere, with what time these two OSes think it is when I boot into either of them.  Apparently one of them thinks that my BIOS is set to use UTC and one of them doesn't.  I'm not sure how to go about figuring out which one is setting the clock correctly (they both use internet time) based on what the BIOS is telling them on boot.  For example, let's say it's noon.  I boot into Windows 7.  Windows 7 thinks it's 6 a.m. until I connect to the internet and update the time.  Then it's fine.  But let's say I then boot into Ubuntu 11.10.  Ubuntu thinks it's 6 p.m. until I connect to the internet and update the time that way.
So, how do I figure out a) what my BIOS is set to (I mean, does it use UTC or not) and b) which OS is getting it right?  (Whenever I boot into either OS, the time is always initially wrong because the prior OS I used has reset the time to its idea of what time it is.)

Ok, figured out this much.  The BIOS reports that it is 12:02 p.m. (the time it was when I booted up my laptop).  Ubuntu reported it as being 6:02 a.m.  So Ubuntu thinks my laptop BIOS is set to UTC, which it apparently isn't.  So:

How do I tell Ubuntu that my laptop BIOS time setting is not set to UTC?  I remember from the installation/setup, but I can't seem to find that option in system settings.  I've just put it on "manual" time adjustment for the time being.

---

