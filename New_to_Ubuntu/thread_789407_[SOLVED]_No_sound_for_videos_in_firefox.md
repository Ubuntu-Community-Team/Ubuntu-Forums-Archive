---
title: "[SOLVED] No sound for videos in firefox?"
date: 2008-05-10
forum: New to Ubuntu
---

### Post by 449 on 2008-05-10
I don't know what's up, this will happen, I'll reinstall flash and it will work for the time being, then the sound will stop working. I checked the sounds tests in Ubuntu and it works fine, and banshee has no problems. Anyone no whatsup?

---

### Post by crashcoredump on 2008-05-10
Since my upgrade last night to 8 I have lost all sound in Firefox as well.
I searched all over FF for some mute setting or preferred sound device but found nothing. All my devices are supported and it works in AlsaMixer and R-box but in the browser there is silence..


I hope we can figure this one out.

Did you recently upgrade FF, what version are you running?

---

### Post by 449 on 2008-05-11
> **crashcoredump said:**
> Since my upgrade last night to 8 I have lost all sound in Firefox as well.
I searched all over FF for some mute setting or preferred sound device but found nothing. All my devices are supported and it works in AlsaMixer and R-box but in the browser there is silence..


I hope we can figure this one out.

Did you recently upgrade FF, what version are you running?

I lost sound shortly after a fresh hardy install.

---

### Post by crashcoredump on 2008-05-11
Here is the fix,

**sudo apt-get install libflashsupport**


The upgrade removes this library unless you choose to keep all unused libraries,

Good Luck!

---

