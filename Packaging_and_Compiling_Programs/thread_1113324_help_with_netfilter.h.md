---
title: "help with netfilter.h"
date: 2009-04-01
forum: Packaging and Compiling Programs
---

### Post by crazysubguy on 2009-04-01
Hi. I've been working on a program that uses netfilter.h  Yesterday morning when I compiled it. It worked great. Then I modified the program and when I used the command ./configure it immediately gave me a warning that netfilter.h is present but not usable. I went ahead and continued hoping the warning was just a warning and my program would still work, but that's not the case. I then deleted the entire directory that my source code was in and untarred the tarball that worked previously.  I still get the warning.  It's just a warning, but when I "make" and "sudo make install", the program runs but it doesn't work. Essentially the functionality part that uses netfilter.h isn't there anymore. The original source tarball worked until yesterday. The one thing I've done in between the working program and the non-working program is I installed a bunch of updates. 

I suspect that somehow yesterday netfilter.h got updated to something newer that doesn't work with my program, but  I don't know how to go back to the previous version.

Anyone have any idea how to make netfilter.h usable?

---

### Post by crazysubguy on 2009-04-01
I figured out my own problem. I could kick myself in the pants for it.

When I modified the original program and compiled it, the binaries went to the same directory as the original, but instead of overwriting the original files, the filename was modified and so the new function was calling the old program. The netfilter warning was just that: a warning.

Anyways I deleted all the binaries I created, recompiled and now it works.

Thanks for getting rid of the yellow and orange theme. I was almost unable to post my original question because my eyes were hurting so bad from the yellow glare.

---

