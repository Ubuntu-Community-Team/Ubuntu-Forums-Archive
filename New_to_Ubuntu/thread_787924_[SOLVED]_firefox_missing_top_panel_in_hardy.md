---
title: "[SOLVED] firefox missing top panel in hardy"
date: 2008-05-09
forum: New to Ubuntu
---

### Post by benner on 2008-05-09
just firefox seems to be affected as far as i can tell.  i have the navigation toolbar and the bookmarks toolbar but the top one to minimize and close is gone.  i have compiz enabled.

(edit) sorry, the bottom panel is missing too.

---

### Post by mgranet on 2008-05-09
It's caused by Compiz, but the fault lies in Firefox. Go into CCSM and go to the Workarounds (Under "Utility") section. Open Firefox, Maximize it, then select the Legacy Fullscreen support option. Close FF, Close CCSM, and the problem should be solved. I've noticed I also have this problem with the OpenOffice suite; same procedure applies.

---

### Post by benner on 2008-05-09
thank you.  it worked.

---

### Post by Toadmund on 2008-05-10
Um,...what is ccsm?

Never mind 'compiz config settings manager'

---

### Post by Nielsoerbaek on 2008-08-03
I had the same problem, only i have no idea what compiz is or how it works. I simply opened my package manager and set all the packages concerning Firefox to re-install. Solved the problem fine.

Good luck.

---

### Post by fenix_nl on 2008-12-03
I had to **disable** Legacy Fullscreen Support to fix the issue.

---

### Post by silverglade00 on 2008-12-03
Ok, I have been looking for a way to fix that for about a year now. I agree with fenix_nl, you have to DISABLE the legacy fullscreen support.

---

### Post by AstronautFarmer on 2009-01-15
I am using Intrepid Ibex and having the same problem. I am new to ubuntu... so sorry if this sounds dumb but how do i get to the CCSM?

---

### Post by benner on 2009-01-17
you need to install it.  it isn't installed by default.

---

### Post by peppered on 2009-01-28
Thanks for the help, disabling legacy also worked for me...maybe it varies on the version  of Firefox you are using?? For those who are new to Ubuntu installing CCSM is easy ...System > Administration > Synaptic Package Manager > In the search type Compiz and look for compizconfi-settings-manager and mark it for install.
Thanks again for the fix...it was annoying me!:(

---

