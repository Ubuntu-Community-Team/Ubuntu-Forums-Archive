---
title: "[bash]read variable to array"
date: 2010-02-03
forum: Programming Talk
---

### Post by munky99999 on 2010-02-03
so basically i start with an array. I then echo question for which one I want.which I bring to a read variable. Then use basically ${array[$variable]}

which works fine.

I wonder though. Is it possible to do something like.

read MUNKY1 MUNKY2 MUNKY3

---

### Post by Brandon Williams on 2010-02-04
With that use of read, the first token would be stored in MUNKY1, the second in MUNKY2, and the rest of the line of input in MUNKY3.

Is that what you're asking?

---

