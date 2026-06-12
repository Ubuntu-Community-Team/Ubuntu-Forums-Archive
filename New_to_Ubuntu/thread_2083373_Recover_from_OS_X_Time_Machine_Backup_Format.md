---
title: "Recover from OS X Time Machine Backup Format?"
date: 2012-11-12
forum: New to Ubuntu
---

### Post by MyTinFoilHat on 2012-11-12
Apparently, When I lept with both feet into Ubuntu, I may have made a stupid mistake. In my haste, I didn't grab files off my Time Machine archives (yes, I hated the OS X experience <i>that much>/i>- and just wanted out ASAP. Anyway...) I figured I'd ask here. *Is* there a way of retrieving files from OSX backup to my nice, clean, user-friendly Ubuntu environment? I figure, if someone knows, someone knows here. PlEEZ tell me I don't have to go to the 'Genius' Gestapo.   Many thanks. Mtfh

---

### Post by Lars Noodén on 2012-11-12
If you install the packages hfsplus, hfsprogs, and hfsutils you should probably be able to mount the partition and read from it.  It might be best if you try mounting read-only so that there is no risk of change.

---

### Post by MyTinFoilHat on 2012-11-12
> **Lars Noodén said:**
> If you install the packages hfsplus, hfsprogs, and hfsutils you should probably be able to mount the partition and read from it.  It might be best if you try mounting read-only so that there is no risk of change.

Cool. I'll give that a shot. TYVM.

---

