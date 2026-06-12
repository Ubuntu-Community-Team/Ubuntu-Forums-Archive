---
title: "VirtualBox"
date: 2008-09-26
forum: New to Ubuntu
---

### Post by johnmata on 2008-09-26
I installed VirtualBox, and then XP onto it.  Every now and again XP freezes before booting up all the way.  I am not sure how to force quit the frozen xp application.  I suppose it would also be nice to keep it from freezing in the first place.  Any advice is greatly appreciated.

---

### Post by Therion on 2008-09-26
> **johnmata said:**
> I installed VirtualBox, and then XP onto it.  Every now and again XP freezes before booting up all the way.  I am not sure how to force quit the frozen xp application.  I suppose it would also be nice to keep it from freezing in the first place.  Any advice is greatly appreciated.
So your setup is Linux hosting a Virtual Box WinXP guest, correct?  Are you using the binary version of Virtual Box or the OSE version?  Hint: If you installed VB from the repo you're using the OSE version.  If that works for you fine, but obviously it's not.  The binary version you can download from the VB website, I would say is your best bet.  It's the more current version if nothing else.   

My suggestion: See what happens after reinstalling your XP Guest.  That would be the easy solution.  If the first suggestion doesn't fix the problem, and you're running the OSE version, then I'd say it's time to un-install Virtual Box from your system entirely, download and install [this version](http://www.virtualbox.org/wiki/Downloads) instead and then re-install your XP guest.

---

### Post by mikewhatever on 2008-09-26
Giving the guest OS more RAM may help. How much RAM is currently allocated to XP?

---

