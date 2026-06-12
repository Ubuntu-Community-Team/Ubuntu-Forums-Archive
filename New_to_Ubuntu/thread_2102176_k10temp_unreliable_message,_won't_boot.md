---
title: "k10temp unreliable message, won't boot"
date: 2013-01-06
forum: New to Ubuntu
---

### Post by Metz on 2013-01-06
I'm recently upgraded to xubuntu 64-bit on my M3A78 PRO running AMD Athlon 7750 Dual.

It's been fine for a few days, but I've now come up against an error on bootup reporting :-

"k10temp: unreliable CPU thermal sensor: monitoring disabled."

At this point it refuses to boot into the desktop. I can Alt-Fn to log into a command line, but that's about it. But even then, it will only run for about 5 minutes before completely freezing up.

This happened once before a few days ago, and I simply rebuilt the machine from scratch. But I can't do that again.

According to the bios....temps are fine. 

Is there anything I can do? I don't really know where to start with this one.

---

### Post by gordintoronto on 2013-01-06
Xubuntu 12.10? Are you sure the CPU is properly seated with no bent pins?

Can you run from a LiveCD or LiveUSB?

---

### Post by Metz on 2013-01-07
> **gordintoronto said:**
> Xubuntu 12.10? Are you sure the CPU is properly seated with no bent pins?

Can you run from a LiveCD or LiveUSB?

Yes, 12.10.
It runs fine from 12.10 Live, both on CD and off USB mem stick.

CPU hasn't been touched and has been runnning fine for about 4 years.

I moved to 12.10 about 5 weeks ago...initially 32bit. Everything was fine for a while. Last week, it failed with the above error. Because it worked from the Live CD, I decided to reinstall, and this time I went for the 64 bit build. Again, everything fine for a few days, then it happened again last night.

Again, I tested with the Live CD and it boots and runs fine for over 1 hour before I switch it off. It also seems to be affecting my bios settings in that it is loosing the 1st/2nd/3rd drive boot sequence.

Could this be related? Could this be caused by either a memory issue or a drive issue?

---

### Post by gordintoronto on 2013-01-07
When you said you "rebuilt the machine from scratch," I thought you meant that you took it apart and put it back together again.

If you run Disk Utility and point at the hard drive, does it say the "Disk is healthy"?

Do you have lm-sensors installed?

---

