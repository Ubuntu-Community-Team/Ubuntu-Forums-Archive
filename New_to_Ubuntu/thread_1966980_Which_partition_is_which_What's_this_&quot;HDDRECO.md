---
title: "Which partition is which? What's this &quot;HDDRECOVERY&quot; partition? (Dualboot Win7+Ubuntu)"
date: 2012-04-27
forum: New to Ubuntu
---

### Post by K0ri on 2012-04-27
I'm looking to expand my Ubuntu partition, but the only partitions shown in GParted are a tiny 1.46gig one called System, my Windows 7 partition, and a weird 14.53gig partition named HDDRECOVERY. (And the unused space of course). My Ubuntu partition is suppose to be 20gigs... which one of these am I meant to be expanding to expand Ubuntu? I don't want any form of "hard disc drive recovery"... I'm confused.
Attached is a screenshot of GParted, and my problem.

---

### Post by Bartender on 2012-04-27
That HDDRECOVERY partition holds a copy of your Windows install.  You've made recovery discs, right?  _IF_ you've made recovery discs, and if they're good, you don't need the HDDRECOVERY partition any more.  

In fact, after you create recovery discs you may be unable to access the partition.  Some manufacturers install some kind of magic tweakery so that you can make one set of recovery discs and then the partition is inaccessible.  Sorta like Mission Impossible, where the message self-destructs.  But in this case, the partition remains there, taking up space, whether you can use it or not...

---

### Post by K0ri on 2012-04-28
So... is the first partition the one I should expand?
If so, why is it reading as being so small?

---

### Post by Mark Phelps on 2012-04-28
You do NOT have a Linux partition!  So, there is nothing to expand.

The first partition is the Win7 boot partition.  If you mess with that, Win7 will not boot anymore.

Had folks looked in detail at your info, they would have seen (1) the lack of any Linux filesystem partitions and (2) the reference to /host in the screenshot.

You have a Wubi installation -- in which you installed Ubuntu from INSIDE Windows.  It is contained in a root.disk file in your "C" partition.

You will have to read through the Wubi Guide below for details on how to expand the space you allocated to Ubuntu:

[https://wiki.ubuntu.com/WubiGuide]("https://wiki.ubuntu.com/WubiGuide")

---

