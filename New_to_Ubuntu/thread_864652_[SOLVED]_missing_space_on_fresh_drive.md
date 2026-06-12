---
title: "[SOLVED] missing space on fresh drive"
date: 2008-07-19
forum: New to Ubuntu
---

### Post by KCormier on 2008-07-19
Howdy all.  I just created an fresh 100 gig logical volume.  I used mkfs to format the whole thing with ext3.  With NOTHING on the drive yet it already has 5.2 gigs used.  Any idea what's up with that?

-Kevin

---

### Post by drs305 on 2008-07-19
I believe mkfs reserves 5% of the space, saving it for special/privileged (root) use.

tune2fs has options to change the amount of reserved space should you wish to do so. The option for changing this is "-m".

You can read the 'man' pages of both for more information about the reserved space.

---

### Post by KCormier on 2008-07-19
That fixed it.  Thanks :)  Went from 5 gigs missing to less than 200 megs :)

---

