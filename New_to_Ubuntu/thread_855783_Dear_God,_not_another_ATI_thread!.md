---
title: "Dear God, not another ATI thread!"
date: 2008-07-10
forum: New to Ubuntu
---

### Post by sydbat on 2008-07-10
Yup.

Mostly, I want to know if there is any solution to yet another ATI "problem" (although I don't think it is so much a problem as an annoyance).

Radeon x600 pro. Runs both the restricted and open drivers equally well. Both drivers do compiz great and allow 3d for most everything. However...

I find that with the restricted driver (fglrx), if I try to play various 'Linux' games in 3d, I get the "flicker" - that is game screen, desktop, game screen, desktop, you get the idea. Fortunately, I am not epileptic. If I use the open driver, this does not happen. However...

With the open driver, many (not all) 3d apps via Wine will not play, or will be very sluggish.

I do not want to have to enable/disable the restricted driver over and over, just to make certain apps work properly. Is there a solution? Or will I have to reboot every time I want to play Sim City 4 RH (or something else 3d in Wine)?

---

### Post by Xerp on 2008-07-10
Try disabling compiz when playing games.

---

### Post by sydbat on 2008-07-10
That simple? Really? I'll let you know if that works.

---

### Post by skrribble on 2008-07-10
This is a problem that I've faced. However, you don't have to reboot everytime.  If you make a copy of each working xorg.conf file, then you can just copy the appropriate one to /etc/X11/xorg.conf and then CTRL+ALT+BKSPC every time you need to change it.  I realize that this is still not an ideal answer, and it doesn't really solve anything, but this is easier that rebooting.

---

### Post by sydbat on 2008-07-10
Yup. It works. Just turning off "Visual Effects" cleared it up. I feel like a dufus.

Thanks for the help.

---

### Post by sydbat on 2008-07-10
One more thing - when I re-enable Visual Effects, Compiz resets to defaults. I have to re-enable cube, etc. Not a biggie, but is there any way of turning Compiz off that saves my settings, so when I turn it back on I don't have to fiddle? Is this what you are talking about skrribble?

---

### Post by RebateFX on 2008-07-20
> **sydbat said:**
> One more thing - when I re-enable Visual Effects, Compiz resets to defaults. I have to re-enable cube, etc. Not a biggie, but is there any way of turning Compiz off that saves my settings, so when I turn it back on I don't have to fiddle? Is this what you are talking about skrribble?

Hit Alt-F2 and type 

compiz --replace 

Then hit Run.

---

