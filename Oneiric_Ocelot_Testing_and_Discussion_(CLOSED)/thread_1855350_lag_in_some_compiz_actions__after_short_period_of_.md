---
title: "lag in some compiz actions  after short period of idle"
date: 2011-10-06
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by mc4man on 2011-10-06
I've seen this here for quite some time & though really a minor issue does bug me.
Basically after not using compiz? for a short period (30 -40 sec) there can be a small lag when using
Most obvious on cube/rotate which currently is unusable so no real care there.
Also seen when moving  an unmaxed window & a bit in wall from keyboard bindings

Had a bug which I invalidated when seeing this also in unity-2d, but now that it no longer occurs in 2d re-opened

Bug with simple test case
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/843383](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/843383)

---

### Post by mc4man on 2011-10-06
thanks - appears that compiz-0.9, at least on this laptop, needs the gpu at full performance for some actions
Setting the card,(nvidia) to max & then no lag. 
Will probably  leave at the default of adaptive, really just a minor thing anyway

Edit: Whether it's a hardware  or 11.10 issue as to why it takes a sec for compiz to work smoothly don't know. Will have to check on 11.04 & see.. The laptop is getting a bit aged anyway..

---

### Post by mc4man on 2011-10-06
It's fine in 11.04 & in unity-2d & Gs in 11.10. Both will bump to full performance when moving windows but do so smoothly

don't have any other nvidia setups to check if just the current hardware or state of the hardware here

Will probably just let the bug go, currently again invalid,  not a big deal anyway
(though it was invalidated for the wrong reason so I may re-open or may not..

---

### Post by mc4man on 2011-10-06
This is one of those laptops with a manufacturer  neutered bios (dell 1300m) so nothing much in bios to change
Plus this series from 3+ yrs ago had potentially defective 8400 chips, actually did burn this one out after 2.5 yrs.
Fortunately this was when Dell was giving away  free 3 yr. in home warranties. 
As that warranty is done not inclined to push the card even though I believe the gpu was given an extra year of coverage (would hate to test my ability to reason with CS 

To bad the cpu can't handle this action - have altered  ondemand's 'threshold  to scale up value' to 75 from kernel default of 95. 
In this particular case doesn't matter, has some advantages elsewhere

---

