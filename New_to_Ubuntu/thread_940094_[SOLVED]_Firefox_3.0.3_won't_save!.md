---
title: "[SOLVED] Firefox 3.0.3 won't save!"
date: 2008-10-06
forum: New to Ubuntu
---

### Post by Gaudentius on 2008-10-06
I don't know how long I've been with this latest version, but I think it was last Thursday (October 2nd) that Firefox wouldn't allow me to save images or links.  You know: you right-click, select Save As, then nothing happens.  I've tried several times since then and nothin' goin'.

Has anyone come up with this problem?  Does anyone have a remedy?

GD:popcorn:

---

### Post by bhadotia on 2008-10-06
Does ctrl+s also does not work.
Also, try saving things from the file menu (Save Page As..) option.

---

### Post by Gaudentius on 2008-10-06
> **bhadotia said:**
> Does ctrl+s also does not work.
Also, try saving things from the file menu (Save Page As..) option.

Any way that I try, the option menu comes up.  But the option to save the file to a location will not come up.

i.e.
Step 1: Right click
Step 2: Save As . . .
Step 3: . . . nothing

or

Step 1: click File
Step 2: Save Page As . . .
Step 3: . . . nothing

Copy image works, set as background works . . .

GD

---

### Post by asmoore82 on 2008-10-06
> **Gaudentius said:**
> Any way that I try, the option menu comes up.  But the option to save the file to a location will not come up.

i.e.
Step 1: Right click
Step 2: Save As . . .
Step 3: . . . nothing

or

Step 1: click File
Step 2: Save Page As . . .
Step 3: . . . nothing

Copy image works, set as background works . . .

GD

create a clean firefox profile and see if the problem still occurs:

from a Terminal or "Run" (Alt+F2):
```
firefox -no-remote -P
```
(that must be an uppercase 'P')

if the problem persists, re-install firefox and/or make sure you have the
`firefox-gnome-support` package installed;
if everything is OK in a new profile, go back to the old one and export your bookmarks to a plain file and migrate to the clean profile permanently.

---

### Post by Gaudentius on 2008-10-06
That worked!

After getting the settings all set up again to make it work at work, everything is fine again.  I'll have to remember that for the next time, which I hope is not any time soon.

Thanks!!!

GD

---

