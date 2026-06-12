---
title: "python curses dependency question"
date: 2009-10-09
forum: Programming Talk
---

### Post by openfly on 2009-10-09
If your environment has libncurses shared libraries but no libcurses shared libraries, will this break the curses module in python 2.3?

---

### Post by openfly on 2009-10-09
setting TERMINFO_DIRS got it to start to display, it drew window outlines, but segfaulted as it began to draw text.

I thought it was a locale problem but my mindless forays into LOCALE environment correction has proved fruitless.

Had anyone ever seen something like that with curses?  Fix ideas?

---

