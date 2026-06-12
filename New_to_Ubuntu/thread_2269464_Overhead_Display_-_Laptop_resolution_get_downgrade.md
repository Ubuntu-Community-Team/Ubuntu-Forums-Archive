---
title: "Overhead Display - Laptop resolution get downgraded?"
date: 2015-03-15
forum: New to Ubuntu
---

### Post by Geoffrey_Arndt on 2015-03-15
This past Saturday, I had to do a demo at local comp. club.   Parts of the demo were on a laptop running windows7, and other parts were on another acer laptop with ubuntu 14.04.   The windows laptop screen matched the overhead display screen in that the whole laptop screen was utilized, but when using Ubuntu, the laptop screen size was downgraded from 1366 x 800 or so, to 1024 x 768 and I had black vertical borders on each side of display.   

I could still complete the demo but is there a way to have ubuntu keep it's 1366 x 800 or even if 1024 x 768, to use the full screen display on laptop without the borders?   

I recall I had to mirror the display (and then received info popup about a change in display size).  (the display projector is a 6 or 7 year old Epson projector,maybe limted to VGA only?)

Hope I haven't confused the issue . . . any tips appreciated!

---

### Post by TheFu on 2015-03-16
I use **lxrandr** to pick the output, then the resolution and freq.
It is pretty easy - but not automatic. Have to manually do this.

It is your choice if you mirror or use 2 displays. If you mirror, both probably should be set to the same resolution - that isn't required, but giving a talk full screen on a 1920x1200 laptop displayed on a 800x600 projector means most of the screen doesn't get displayed on the projector.

---

### Post by Geoffrey_Arndt on 2015-03-16
I think the Epson projector can do at least 1366 x 768 (which is the native resolution for my Acer Timeline laptop).   So - thanks to your suggestion, I'll certainly check out "lxrandr".   Might you happen to know if those settings are retained, or should the reso be set for each demo session?

Thanks.

ga

---

### Post by TheFu on 2015-03-16
I always have to manually set it at the start of every hook-up/presentation. There is a save button - doesn't seem to work, at least it never has the last 5+ yrs for me.

Of course, you can use xrandr or arandr too - just different interfaces to xrandr. I find lxrandr to be simple, effective and lite.  Don't forget that some projectors also mandate specific frequencies - I was burned in front of 250+ people at YAPC last year with that one. They had a fancy 3 projector, plus streaming, plus capture setup and 1 part of that only worked with 60hz even though 2 of 3 projectors were fine.

---

