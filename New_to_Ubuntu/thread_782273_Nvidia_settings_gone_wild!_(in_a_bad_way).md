---
title: "Nvidia settings gone wild! (in a bad way)"
date: 2008-05-04
forum: New to Ubuntu
---

### Post by brentmi Sato on 2008-05-04
Recently installed Heron, set up my dual monitors with nvidia settings, had no problems for a few days... then I had to restart.

My usual settings are separate X screens, no Xinerama,  screen 0 at 1024x768@ 70hz, screen 1 at 1280x1024@75hz, screen 1 to the left of 0, bottom edges lined up by putting screen 0 into absolute positioning.

After restart, I was shown a Xinerama enabled desktop at a resolution so huge I had to get right up to the screen to see anything, and I had to scroll around to find my terminal...  well, put it this way, everything was hard-to-impossible to get to, the screens had a huge deadspace between them.  I managed to get nvidia settings running (I'm also having the problem where when it starts it's very small, btw) and adjust things so I could get them back to some semblance of how I want them.  Saved to the xorg.conf file.

So once I did, I restarted the x-server.  Once I logged back in, screen 1 had been moved to the right of 0, it's resolution had been set to auto (which it defaulted to something very high/unusable) while screen 0 had been left pretty much alone, except that it was now lined up with the top edge of screen 1.

Skip forward:  Every time I restart x-server/log out/restart/shut down and come back, I come into something different and seemingly random every single time.  I've come into Xinerama desktops so insanely huge I'd probably need a projector and an exterior wall to see it all at once, and I've come into resolutions akin to old televisions, with my mouse pointer about four inches tall.   Usually it's just that the positioning is moved and resolutions change. Anytime I try to fix it, and no matter how (through nvidia-settings, manual editing), I'm pretty much ignored and come in to a new adventure.  I've even started from a new xorg file.  But no matter what happens, the screens will only ever line up at the top instead of the bottom.

I'm out of ideas, and rather frustrated.

---

### Post by chewearn on 2008-05-05
Can you post xorg.conf?

---

### Post by alienexplorers on 2008-05-05
When you set up your dual monitors did you use nvidia-settings.  If so did you run it in root mode.
> sudo nvidia-settings

---

