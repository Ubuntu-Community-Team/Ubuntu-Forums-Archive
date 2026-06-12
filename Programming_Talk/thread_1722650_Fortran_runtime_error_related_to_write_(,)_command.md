---
title: "Fortran runtime error related to write (*,*) command"
date: 2011-04-06
forum: Programming Talk
---

### Post by castiglione on 2011-04-06
Hello, all.
 
I recently compiled a f95 program; it compiled fine but when I tried to run it, I got this error message:
 
**At line xx of program yyyyyy.f (unit=6, file='stdout')**
**Fortran runtime error: Insufficient data descriptors in format after reversion**
 
line xx in question was:
 
**      write (*,10) "Intro"**
 
with the formatting line being:
 
**10   format (t33)**
 
I'm guessing this may have something to do with the default output for write being to something other than the terminal but I'm stuck at this point.
 
Anyone have any ideas as to what I'm doing wrong?
 
Thanks in advance!
 
c

---

### Post by bouncingwilf on 2011-04-06
Your output format t33 just specifies that the "cursor" is tabbed to position 33 across the screen before output starts, you now need to add a format descriptor for the text string (used to be something like 4H in the old days) for your string but I suspect f95 has a "new improved" descriptor.


Bouncingwilf

---

