---
title: "[SOLVED] Checking for Inotify support?"
date: 2008-10-04
forum: Programming Talk
---

### Post by tigrezno on 2008-10-04
How can i check within a C program if inotify support is enabled?

Can i check it within the makefile?

thanks!

---

### Post by tigrezno on 2008-10-04
Right now, i solved it by adding a second target in my Makefile, so enabling inotify support is a user decision.

for example:

$(target)-inotify:
    gcc test.c -o test -DHAVE_NOTIFY

and then in test.c i have:

#ifdef HAVE_NOTIFY
#include <sys/inotify.h>
#endif

(it works for me but i don't know it that's correct)

---

