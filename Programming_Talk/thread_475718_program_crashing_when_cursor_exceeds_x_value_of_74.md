---
title: "program crashing when cursor exceeds x value of 74"
date: 2007-06-16
forum: Programming Talk
---

### Post by yurimxpxman on 2007-06-16
Could someone please help me figure out why my program is crashing when the cursor reaches the x value of 75? It's a bit too complicated for a paste bin, so I put the tarball [here](http://yurimxpxman.dyndns.org/karlie.tar.bz2). It's not giving me a segmentation fault or anything. It just quits.

I'm trying to figure out how to use gdb at the moment, so pointers on that would be welcome too if you have any.

Thanks,

Josh

**Edit:** I got it working. I put **return 0;** after each possibility for the value of getch() in order to avoid proceeding to the option to quit the program. I still have no idea why it was doing this, though.

---

