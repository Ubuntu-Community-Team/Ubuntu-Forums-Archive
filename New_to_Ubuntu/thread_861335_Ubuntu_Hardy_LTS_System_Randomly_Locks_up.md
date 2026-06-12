---
title: "Ubuntu Hardy LTS System Randomly Locks up"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by Divider on 2008-07-16
The issue I am Having is a VERY random system lockup.

It varies, and there is no root of the problem.

I could run ANY program, and at ANY time. It will lock up.

Sometimes it will go a good 20-30 mins without a lockup, other times it will only last 5.

Doesn't matter how heavy the workload is, something simple like running firefox or somthing heavier like compiling.

Any help / advice would be VERY appreciated.

I've installed all updates, tried reinstalling about 3-4 times, and have had no luck.

-Divider

---

### Post by OffAxis on 2008-07-16
sounds like a hardware issue; RAM, hard drive, power supply, or motherboard would be the most likely culprits. Could also be a thermal issue.

I'd start with the easy stuff; boot to the BIOS screen and have it just sit there for a while and see if it locks up. After that I'd run memtest, then a hard drive scan, then crack your case open, clean out the dust bunnies, and look for any obvious defects (like a capacitor leaking or a discolored spot on the motherboard).

If nothing turns up you could swap out the power supply for a known good one and see if that fixes it.

---

### Post by Divider on 2008-07-30
> **OffAxis said:**
> sounds like a hardware issue; RAM, hard drive, power supply, or motherboard would be the most likely culprits. Could also be a thermal issue.

I'd start with the easy stuff; boot to the BIOS screen and have it just sit there for a while and see if it locks up. After that I'd run memtest, then a hard drive scan, then crack your case open, clean out the dust bunnies, and look for any obvious defects (like a capacitor leaking or a discolored spot on the motherboard).

If nothing turns up you could swap out the power supply for a known good one and see if that fixes it.


Well figured out the problem, it turns out that when i downloaded the hardy cd, something in the iso got corrupted.

:guitar:

---

