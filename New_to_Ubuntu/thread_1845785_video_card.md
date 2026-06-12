---
title: "video card"
date: 2011-09-17
forum: New to Ubuntu
---

### Post by anewguy on 2011-09-17
My desktop is currently using the internal video adapter - ATI Radeon 4200 with the flgrx driver.  I know of the problems with ATI drivers, so I guess I shouldn't be surprised that enabling special effects in 11.04 wouldn't be the best.  A little history:

In 10.xx, compiz worked great - the cube and all the other eye candy.  Then I installed 11.04.  Not a fan of Unity at this time, so I tried Ubuntu Classic - the one with effects.  Installed compiz settings manager and tried enabling the cube, etc., but my desktop a started being too large for my display and other strange things.  Okay, eye candy not that important, so I selected Ubuntu Classic - No Effects.  This seems to work fine for the most part.

So.......I was looking in 1 of my hardware junk boxes for a cable to use on the Wii gaming console, and I found a video card I bought earlier this year.  It's an ATI again - this time an ATI Radeon HD 3450 PCI-e card.

Does anyone know if I'll have better luck with that card (e.g., a better driver than flgrx?)?  When I installed the old card I went through Additional Drivers and it said the flgrx driver was available and I needed to enable it (which I did).

Any thoughts would be greatly appreciated!

Dave ;)

---

### Post by searchfgold6789 on 2011-09-17
Stick with the 4200! It is much better. Also I doubt you will have better luck as far as drivers go with the older one.
Try changing your composting type.
And then send the other one to me!!! :popcorn:
 - search

---

### Post by sandyd on 2011-09-18
> **anewguy said:**
> My desktop is currently using the internal video adapter - ATI Radeon 4200 with the flgrx driver.  I know of the problems with ATI drivers, so I guess I shouldn't be surprised that enabling special effects in 11.04 wouldn't be the best.  A little history:

In 10.xx, compiz worked great - the cube and all the other eye candy.  Then I installed 11.04.  Not a fan of Unity at this time, so I tried Ubuntu Classic - the one with effects.  Installed compiz settings manager and tried enabling the cube, etc., but my desktop a started being too large for my display and other strange things.  Okay, eye candy not that important, so I selected Ubuntu Classic - No Effects.  This seems to work fine for the most part.

So.......I was looking in 1 of my hardware junk boxes for a cable to use on the Wii gaming console, and I found a video card I bought earlier this year.  It's an ATI again - this time an ATI Radeon HD 3450 PCI-e card.

Does anyone know if I'll have better luck with that card (e.g., a better driver than flgrx?)?  When I installed the old card I went through Additional Drivers and it said the flgrx driver was available and I needed to enable it (which I did).

Any thoughts would be greatly appreciated!

Dave ;)
ATI Radeon HD 3400
Chip: RV620
Core Clock: 600MHz at full power (no powerplay)
Memory: 256mb DDR2 clocked at 500MHz

ATI Radeon HD 4200
Chip: RS880
Core Clock: 500MHz at full power (no powerplay)
Memory: Shared, up to 512mb system + optional 128 sideport clocked at ??? (800MHz I think)

Take your pick. Assuming the HD4200 is the IGP shared version. I could go on about pixel bandwidth and whatnot, but its just gonna get boring by then...

P.S. The sideport is a extra stick of memory in the computer that was created in an attempt to speed the graphics up a bit. Check if your mobo has one.

---

### Post by anewguy on 2011-09-18
I was *hoping* someone could give me better news than what I already thought - it's a Radeon, so it will use the same driver.  I disbled the restricted driver from ATI for now, but I know if I want to do some of the eye candy I'll need to get 3D working again.

At any rate, thanks!

Dave ;)

---

### Post by sandyd on 2011-09-18
> **anewguy said:**
> I was *hoping* someone could give me better news than what I already thought - it's a Radeon, so it will use the same driver.  I disbled the restricted driver from ATI for now, but I know if I want to do some of the eye candy I'll need to get 3D working again.

At any rate, thanks!

Dave ;)

Try some of the builds from the xorg-edgers overlay. I compile mesa from svn here, and while running on gallium, it outperforms fglrx in most things (KDE can sometimes be a PITA in graphics performance...)

---

