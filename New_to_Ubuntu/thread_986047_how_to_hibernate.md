---
title: "how to hibernate"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by stonecoldjha on 2008-11-18
i know this might sound stupid.but,i want to know as to how i can make ubuntu hibernate,i mean i select "quit" and click on hibernate.but,then how do i restore it back from the hibernation?

---

### Post by starcannon on 2008-11-18
Assuming your computer is happy with the default power management utility scripts, you should be able to just turn the computer on and boot into the same state it was in when you chose hibernate. This requires of course that your /swap partition is >= the amount of ram that you currently have installed in your machine, and that your bios is supported by default in the power management scripts. If you added ram since the install, or if your swap file is to small for whatever reason, then you can use a gparted liveCD to expand it; if your bios doesn't "just work" with the default hibernation scripts then your going to have to tweak the scripts. My understanding is that Ubuntu 9.04 is going to try to address power management, though I picked that up in forums, so take it with a grain of salt.

I know this isn't likely the concise and definitive answer, but what I've posted should point you in the right direction; if your like me, half the battle is knowing what questions to ask, after that answers generally come easy.

---

### Post by stonecoldjha on 2008-11-18
i have 2 gigs of RAM,but only 400 MB of swap.so may be this is the reason why i can't make it work.i shall resize the swap partition.

---

