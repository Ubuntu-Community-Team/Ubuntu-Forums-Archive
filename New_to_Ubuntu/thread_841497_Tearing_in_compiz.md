---
title: "Tearing in compiz"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by occams_beard on 2008-06-26
Hello,

The one thing that's keeping me from moving to Ubuntu completely is the horizontal tearing I get when moving a window, scrolling, etc. I know its a little thing, but it annoys the heck out of me.

This tearing occurs with or without compiz effects enabled.  I can mitigate the tearing effect somewhat by going into the advanced compiz settings (ccsm) and enabling "sync to vblank" and increasing the refresh setting to 100... but even then it's still tearing pretty bad.

Is there anything I can do to get rid of this tearing once and for all?  My video card is an onboard intel X3100.

---

### Post by sdennie on 2008-06-26
Have you tried manually setting the refresh rate in ccsm to 60?  That's usually the correct value for an LCD.  Also, make sure "Automatically Detect Refresh Rate" is disabled.

---

### Post by philinux on 2008-06-26
I'm getting this, didn't know the technical term.

Jaggy lines at about 20 degrees opening a window, before the proper screen appears.

Doesn't happen all the time. I thought it as my graphics card.

Done the advice above, better but still there.

---

### Post by sdennie on 2008-06-26
> **philinux said:**
> I'm getting this, didn't know the technical term.

Jaggy lines at about 20 degrees opening a window, before the proper screen appears.

Doesn't happen all the time. I thought it as my graphics card.

Done the advice above, better but still there.

Did you enable sync to vblank in ccsm?  If so and you still get that, if you are using nvidia and have enabled global anti-aliasing, it used to cause behavior similar to what you are describing.

---

### Post by cespinal on 2008-06-26
Interesting... I thought my computer was not fast enuff for compiz... I'll check this out when I get home

---

### Post by philinux on 2008-06-26
> **vor said:**
> Did you enable sync to vblank in ccsm?  If so and you still get that, if you are using nvidia and have enabled global anti-aliasing, it used to cause behavior similar to what you are describing.

Not sure I've enabled anything to do with anti-aliasing

---

### Post by occams_beard on 2008-06-26
> **vor said:**
> Have you tried manually setting the refresh rate in ccsm to 60?  That's usually the correct value for an LCD.  Also, make sure "Automatically Detect Refresh Rate" is disabled.

Yeah, tried that. It's really bad at 60, which is indeed my monitor's refresh rate.  No idea why, but setting it to 100 in ccsm decreases the tearing effect a bit.  This gave me hope that it might be fixable. 

BTW, under Vista's Aero interface the display is smooth and no tearing whatsoever.

---

