---
title: "Broken 8.04"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by carusoswi on 2008-05-10
So, I've been running 8.07 for a while, now.  It's up to date.  Yesterday, when I booted up, the desktop arrived with other than the elephant skin which I have selected . . . east ebough to fix. But, I also noticed that none of my drives showed on the desktop, and navigation to those drives was met with error messages.

Work around was to reboot from recovery mode and allow the system to do a FSCHK.  Errors occured on many (if not all) entries in my CrossOver directory.  Other than that, I hav no issues to date.

Not certain if or why I need to reapply, but would be curious what y'all can advise on that subject as well.

Thanks.
Caruso

---

### Post by Paqman on 2008-05-15
You should never run fsck on a mounted disk. If you need to run it in future, do it from the LiveCD, since that leaves your hard drive unmounted.

---

### Post by carusoswi on 2008-05-16
> **Paqman said:**
> You should never run fsck on a mounted disk. If you need to run it in future, do it from the LiveCD, since that leaves your hard drive unmounted.

Can you explain in more detail, please?  I just did what Ubuntu suggested I do - didn't really know why I had a problem or what else to do about it.  Seems to have worked out fine - my crossover applications had turned to toast, anyhow - none of them would run.

Since running FSCHK, Crossover is working, although I had to reinstall all of my Windows applications.  Except for MS Office (especially Access and to a lesser extent, Excel, there is no other MS ap that I need that actually runs in Crossover).

Anyhow, the fschk worked and my machine booted up.  Still don't know what went wrong, however.

Caruso

---

