---
title: "One disc drive not detected in Ripper X &amp; computer freezes when DVD inserted"
date: 2011-12-23
forum: New to Ubuntu
---

### Post by lpfreak1170 on 2011-12-23
Using 10.04.

I have 2 disc drives.  Drive D (sorry for the Windows speak) is read/burn, while drive E is only read.  In XP, I use E as my reading/playing/ripping drive with no problems and use D to only burn.  In Ubuntu, Ripper X will not recognize E (although Rhythmbox will), and inserting a DVD (either data or video) in E causes my computer to completely freeze up (but DVDs play and rip fine in D).  Please help.

I've just been living with this for over a year now, but I would love to get this solved and eventually more than likely go all Ubuntu.

---

### Post by lpfreak1170 on 2012-01-06
Bumping up.

---

### Post by John Peschken on 2012-01-06
> **lpfreak1170 said:**
> Using 10.04.
 
I have 2 disc drives. Drive D (sorry for the Windows speak) is read/burn, while drive E is only read. In XP, I use E as my reading/playing/ripping drive with no problems and use D to only burn. In Ubuntu, Ripper X will not recognize E (although Rhythmbox will), and inserting a DVD (either data or video) in E causes my computer to completely freeze up (but DVDs play and rip fine in D). Please help.
 
I've just been living with this for over a year now, but I would love to get this solved and eventually more than likely go all Ubuntu.
 
This sounds like the problem I had with a generic USB CD drive I used to own.  The problem was with the particular interface chip in the CD Drive.  Ubuntu would not deal with it.  The problem went away some time between 10.04 and 11.04.  Apparently they fixed the bug.  I don't have the details any more, but I guess what I'm saying is that it may be incompatible with Ubuntu.  
 
More hardware information might be helpful to someone more knowledgeable than I am.  What can you tell us about the drive and it's internals?  What version of Ubuntu are you running?

---

### Post by lpfreak1170 on 2012-01-06
Thanks for the reply.

I'm running Ubuntu 10.04 (lucid).  My read/write drive (dev/sr0) is an Asus DRW-2014L1, and my read drive (dev/sr1) is an Asus DVD-E818A.  Unfortunately, I don't know about the internals of the drives.  My pata host adapter (if it helps) is a Marvell 88SE6101 single port PATA133 interface.

---

