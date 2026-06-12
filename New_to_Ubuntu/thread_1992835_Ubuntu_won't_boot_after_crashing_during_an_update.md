---
title: "Ubuntu won't boot after crashing during an update"
date: 2012-06-01
forum: New to Ubuntu
---

### Post by OccamsChainsaw on 2012-06-01
So a few days ago, I started installing some recommended upgrades...quite a few because I tend to blow these off and install huge batches at once. Anyway my computer was about halfway done when it locked up, as it's been known to do in the past when I'm have many memory-intensive processes going all at once. Only this time, after a hard restart, I couldn't boot Ubuntu. After the Ubuntu Studio flash screen, i get a black screen with white text that says "Checking (various things, battery state, etc.)" and then "[OK]", and then it stops here. 

I'm completely new to this, but here's what i've tried so far:

-updating GRUB bootloader from recovery mode--no luck
-memory test--everything checked out
-repairing broken packages from recovery mode--tells me some updates can;t be retrieved because of insufficient disk space (which I kind of doubt), but seems to be getting some updates.  Most of the text whizzes by, but at the end it gives me a list of error messages saying things like "W: Failed to fetch [http://etc](http://etc).. Could not resolve etc..." Still no luck after the reboot.

Any suggestions would be hugely appreciated. I will update this as I make more desperate attempts.


btw, I'm running version 11.04. Any suggestions are hugely appreciated.

---

### Post by wilee-nilee on 2012-06-01
Boot the live cd, open gparted and look if the HD is full.

---

