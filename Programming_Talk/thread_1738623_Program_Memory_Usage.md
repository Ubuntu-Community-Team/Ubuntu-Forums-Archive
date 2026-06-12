---
title: "Program Memory Usage"
date: 2011-04-25
forum: Programming Talk
---

### Post by DBQ on 2011-04-25
Hi Everybody.

I am trying to measure the memory consumption of my C++ program. I am using VmPeak as my metric.

My problem is that I observed some strange memory patterns. When the main data structure of the program grows the biggest, the VmPeak is often lower then for the cases where the structure is significantly smaller.  Why is that?  Also, would you suggest a better metric for measuring memory usage of my program?

---

### Post by conradin on 2011-04-25
Guessing here, I would prolly need to know how much ram you have, if anything goes to swap when your array goes to infinity or however large it gets. Maybe its being writen to swap? Is it being used or just stored? I seem to recall some OS function to put away mem space which isnt in use, but my OS class was like 6 years ago...

---

### Post by DBQ on 2011-04-25
Thanks for the reply. The structure is both, used and stored.

---

### Post by DBQ on 2011-04-25
Oops, sorry for double posting...

---

