---
title: "[SOLVED] screensaver freezes totally"
date: 2008-09-21
forum: New to Ubuntu
---

### Post by lazylew on 2008-09-21
I'm using Ubuntu Hardy Heron

my screensaver freezes totally after a while

I worked around this by setting the screensaver to not start unless a long inactivity, but when I'm away from the pc for say 2 hours (like when I fell asleep today earlier on;-)) the damage is done again

nothing helps, because the keyboard is inactive then too (I can tell by numlock and capslock) and even ctrl alt del or ctrl alt backspace do nothing so I have to use the cold start button, which I believe for UNIX, and thus for Linux systems too, can be very dangerous 

apart from deactivating the screensaver completely, any solutions for this?

---

### Post by phidia on 2008-09-21
If you have any visual effects enabled (look in System > Preferences > Appearance)
disable them and see if that stops the freezing.

---

### Post by waspbr on 2008-09-21
just outta curiosity, what graphics card do u have?

---

### Post by lazylew on 2008-09-21
> **phidia said:**
> ...visual effects enabled (look in System > Preferences > Appearance)...
those were already disabled

---

### Post by k33bz on 2008-09-21
out of curiousty which screensaver application are you using? As well as which screensavers do you have enabled to run within the screensaver application?

---

### Post by lazylew on 2008-09-21
> **waspbr said:**
> just outta curiosity, what graphics card do u have?
graphics or video card are the same thing, I guess?
in which case:
sis 650_651_M650_740

---

### Post by Kevbert on 2008-09-21
Does the same screensaver fail every time ?  I set mine to random and found one (braid) would always lock up the PC.  If others work OK you can remove the problem one.

---

### Post by PocketDog on 2008-09-21
I had this today actually, using the Flurry screensaver. I hate forced shutdowns so I disabled my screensaver and set the screen to turn off instead (using power options). I don't want to have to do that again... ATI Radeon X1250 here by the way, they're not exactly reliable using the proprietary drivers

---

### Post by lazylew on 2008-09-21
> **Kevbert said:**
> Does the same screensaver fail every time ?  I set mine to random and found one (braid) would always lock up the PC.  If others work OK you can remove the problem one.
it's the one that mixes all sorts, yes, called "random"
it works good for a while, like 20 to 25 minutes or so, before it freezes everything

---

### Post by lazylew on 2008-09-21
> **k33bz said:**
> out of curiousty which screensaver application are you using? As well as which screensavers do you have enabled to run within the screensaver application?
oops - almost overlooked your post... 
it's the default screensaver that comes with ubuntu hardy heron
setting on random

---

### Post by Kevbert on 2008-09-22
> **lazylew said:**
> it's the one that mixes all sorts, yes, called "random"
it works good for a while, like 20 to 25 minutes or so, before it freezes everything

Right, random uses all installed screensavers. If you think you know the exact one that causes the PC to lock up, just run that one on it's own to prove it is at fault. 
Perform a reboot/reset and select random again for screensavers.
With the desktop displayed press Alt-F2 and enter gconf-editor in the box and select run.  Now go to /apps/gnome-screensaver (double click on apps to expand). Now in the right-hand window scroll down to themes and double click on themes to get a new window.  Scroll down in the Values box until you find the troublesome screensaver, highlight it with the mouse and select remove. Select OK and close all windows.
Unfortunately every time the screensavers are updated with a newer release version you'll need to do this.

---

### Post by lazylew on 2008-09-22
> **Kevbert said:**
> Right, random uses all installed screensavers. If you think you know the exact one that causes the PC to lock up, just run that one on it's own to prove it is at fault. 
Perform a reboot/reset and select random again for screensavers.
With the desktop displayed press Alt-F2 and enter gconf-editor in the box and select run.  Now go to /apps/gnome-screensaver (double click on apps to expand). Now in the right-hand window scroll down to themes and double click on themes to get a new window.  Scroll down in the Values box until you find the troublesome screensaver, highlight it with the mouse and select remove. Select OK and close all windows.
Unfortunately every time the screensavers are updated with a newer release version you'll need to do this.
I don't think it's one particular screensaver, because the frozen pictures were clearly very different.
I will set the screensaver to one of those and try out your workaround though. Thanks for the pointers on how to do it.

---

### Post by lazylew on 2008-09-23
> **lazylew said:**
> I don't think it's one particular screensaver...
Turns out it must be one (or some?) particular one(s), because I tested "cosmos" and it doesn't freeze.

This is good enough for me right now; gives me more time to figure out other basic Linux stuff I haven't figured out yet :)

I'll leave that workaround till I get tired of the present screensaver, and I'm keeping the well appreciated notes.

---

### Post by miscellanyous on 2008-09-25
Thanks a lot, Kevbert for your solution.

I also had this problem with the screensaver (and screensaver preview) freezing the desktop. The problematic screen saver was "Molecule" - all the other ones work fine.

My system: Ubuntu 7.10, GNOME 2.20.0
graphics card: ATI rage 128
driver: ati

---

### Post by Sidney232 on 2008-12-24
Yes, I found out that 'molecule' totally freezes everything for me too. I'm a but stuck now because if I open up the Screensaver window to change it the little demo version locks everything up too.
Does anyone have any nice terminal commands to change screensavers?
And to delete 'molecule' from the list available?

---

### Post by PeterCat on 2009-01-20
I'm having the same problem with "Molecule" locking up the preview window. Any ideas?

---

### Post by Sidney232 on 2009-01-21
Yes, I managed to solve this 'molecule' problem the next time I rebooted my PC. I went to the setup and changed screen saver and it wasn't a problem. I think I may have clicked another screen saver before the molecule demo got going properly.

---

### Post by karasu337 on 2009-12-10
Just to add to the data gathering process.  GLMatrix was mine.  And I had full visual effects running.  But it didn't happen every time.

---

