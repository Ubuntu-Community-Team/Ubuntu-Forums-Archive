---
title: "cannot allocate resources (on boot) solved"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by jeepfreak2002 on 2008-04-23
I kept getting errors on an AMD X2 Shuttle XPC on boot.

I built 2 identical boxes.  1 booted fine, and the 2nd was problematic.  I had to update the BIOS and downclock the RAM to DDR667 to get stability on both.  The second machine began hanging on boot, it would hang for a while ticking:

[ 15.742871] PCI: Cannot allocate resource region 7 of bridge 0000:00:06.0
[ 15.742922] PCI: Cannot allocate resource region 8 of bridge 0000:00:06.0
[ 15.742970] PCI: Cannot allocate resource region 7 of bridge 0000:00:07.0
[ 15.743017] PCI: Cannot allocate resource region 8 of bridge 0000:00:07.0

etc

Anyways, after reinstalling and updating everything, I remembered a problem that I had installing Ubuntu on my home PC.  Basically the RAM ended up not being compatible with Ubuntu NOT Windows I wondered if this could be happening again, so I replaced the Corsair XMS RAM with Crucial Balliustix DDR800 RAM (once again downclocked to DDR667, due to the XPCm not Ubuntu)  

The result??  Booted like a charm!!!!

There is something unique in how Ubuntu utilizes the system memory, and the integrated memory controller on the AMD CPU seem to be very finicky...

So the take home message is if you are having unexplainable probs with Linux (and not necessarily Windows) and you are on an AMD based system - try Crucial memory.  It is 2 for 2 in solving my system problems.  I will never buy any other RAM brand.  EVER.  Crucial just works.


I hope that this helps someone!

---

### Post by ZabiGG on 2008-05-16
Highly informative, thanks ;)

To mark your post [SOLVED], just click on the Thread Tools link right above, and choose Mark Thread Solved.

Thanks ;)

---

