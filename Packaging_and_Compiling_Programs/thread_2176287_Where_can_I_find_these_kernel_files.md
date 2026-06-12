---
title: "Where can I find these kernel files?"
date: 2013-09-23
forum: Packaging and Compiling Programs
---

### Post by Bill_Vance on 2013-09-23
Howdy;

I've just gotten the 12.04 source for the kernel, (linux-source-3.2.0),
and There seems to be some files missing.  They are what I'm
needing to put a device driver together, and are:

   stk1160.h  and  stk1160-reg.h

However, they are completely AWOL.

Does anyone know where I can get them?

Bill

---

### Post by whitesmith on 2013-09-23
The kernel is not part of Ubuntu. Try Torvald's postings on GitHub, perhaps [https://github.com/torvalds/linux](https://github.com/torvalds/linux) might be what you're looking for. By the way, this is anything but a posting for Absolute Beginners!

---

### Post by oldos2er on 2013-09-23
Moved to Packaging & Compiling Programs.

---

### Post by Doug S on 2013-09-23
I wonder if those files are not part of the 3.2 series kernel.
I see stk1160.h in the 3.12, 3.11  and 3.10 series sources.
I only see stk1160-reg.h in the 3.12 source.

... Doug

Edit: your post seems to have moved while I was typing.

---

### Post by Bill_Vance on 2013-09-23
> **whitesmith said:**
> The kernel is not part of Ubuntu. Try Torvald's postings on GitHub, perhaps [https://github.com/torvalds/linux](https://github.com/torvalds/linux) might be what you're looking for. By the way, this is anything but a posting for Absolute Beginners!

Sorry about that, but it seemed to be the one category that fit best.  In case
you haven't guessed, I'm kinda new to this site.  Thanks for the link, I'll check
it out.

Bill

---

