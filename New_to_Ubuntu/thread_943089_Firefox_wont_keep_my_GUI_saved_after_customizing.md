---
title: "Firefox wont keep my GUI saved after customizing"
date: 2008-10-09
forum: New to Ubuntu
---

### Post by Lateforgym on 2008-10-09
Im not sure why it suddenly decided to act funny, maybe because I upgraded to 8.10 but the address bar doesnt appear in Firefox and when I re-fix it to the way I want it, after I shut it down and restart, I keeps undoing my customization and throwing things on different bars. I noticed Firefox is running weird on my desktop too, but that was even before the 8.10 upgrade.Perhaps a reinstall?

---

### Post by SunnyRabbiera on 2008-10-09
yeh its probably an issue with ibex, I would not be using it as a standard install if I were you.
I would just use hardy until ibex is final.

---

### Post by kerry_s on 2008-10-09
> **Lateforgym said:**
> Im not sure why it suddenly decided to act funny, maybe because I upgraded to 8.10 but the address bar doesnt appear in Firefox and when I re-fix it to the way I want it, after I shut it down and restart, I keeps undoing my customization and throwing things on different bars. I noticed Firefox is running weird on my desktop too, but that was even before the 8.10 upgrade.Perhaps a reinstall?

sounds like the profile is messed up.
open nautilus, press> ctrl+h
rename .mozilla to .mozilla.bak

that will start you with a new profile, as if you opened it for the first time.

---

### Post by Lateforgym on 2008-10-09
Yea, Im thinking this might be a tab mix plus issue. 

I got it to work then when I hit checked off the clear prior pages visted tab it reset again. 

I think tab mix plus has issues with multiple desktops cause if I try to open FF in another desktop it wanted to jump back to the original desktop I opened it in. It a try to get around that there are still issues, I forget what, but if I remember right when you close out of FF in one desktop it closes out all desktops....maybe I just need to close that like its a tab...

---

### Post by Lateforgym on 2008-10-11
Can someone help me with the follwing command?


open nautilus, press> ctrl+h
rename .mozilla to .mozilla.bak

Is nautilus = Terminal? and is it just "ctrl+h" that I press?

Also how do you rename .mozilla to .mozilla.bak?

Thanks

---

### Post by kerry_s on 2008-10-11
> **Lateforgym said:**
> Can someone help me with the follwing command?


open nautilus, press> ctrl+h
rename .mozilla to .mozilla.bak

Is nautilus = Terminal? and is it just "ctrl+h" that I press?

Also how do you rename .mozilla to .mozilla.bak?

Thanks


nautilus is the file manager if your using gnome, usually named "home"

ctrl+h shows the hidden files in nautils

right click .mozilla, select rename

if you rather do it in terminal its:
mv ~/.mozilla ~/.mozilla.bak

---

