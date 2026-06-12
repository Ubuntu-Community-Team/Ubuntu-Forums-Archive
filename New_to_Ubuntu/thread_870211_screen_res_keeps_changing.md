---
title: "screen res keeps changing"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by t0p on 2008-07-25
Since I installed Hardy (a week or so ago) my monitor's resolution keeps changing - sometimes 1280 x 1024, sometimes 800 x 600.  Is this a bug I'm just gonna have to get used to?  Or is there a fix?

---

### Post by candtalan on 2008-07-25
May I throw a guess in? If the resolutions in xorg.conf are not quite appropriate (or recognised correctly(?)) I have read somewhere that the resolution is dropped back, or rolled around, maybe to the end of the list(?) 

Not at all sure about this. I am still a bit confused by exactly how the xorg.conf works in 8.04.

---

### Post by coffeecat on 2008-07-25
Did you have your monitor switched off, or disconnected, when you booted up and landed in 800x600? If the xserver can't detect a monitor, it will default back to 800x600.

If this happens to you, you don't have to reboot. Just restart the xserver with ctrl-alt-backspace or log out and in again.

I discovered this when using two machines connected to one monitor through a KVM switch. Every time I booted up one machine while continuing to work with the other I got this. It took me a long time to figure out what was happening. :|

---

### Post by t0p on 2008-07-25
> **coffeecat said:**
> Did you have your monitor switched off, or disconnected, when you booted up and landed in 800x600? If the xserver can't detect a monitor, it will default back to 800x600.


Yes! As I remember, I switched on the monitor some time after I turned the computer on.

I'll have to do it again just to check. **Thanks** coffeecat!

---

