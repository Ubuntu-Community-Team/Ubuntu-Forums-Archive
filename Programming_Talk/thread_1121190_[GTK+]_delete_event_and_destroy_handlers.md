---
title: "[GTK+] delete_event and destroy handlers"
date: 2009-04-09
forum: Programming Talk
---

### Post by Jesdisciple on 2009-04-09
I recently began adapting my CLI program to GTK and finally narrowed my compile-time bugs to these:```
interface.c: In function &#8216;start&#8217;:
interface.c:367: error: &#8216;delete_event&#8217; undeclared (first use in this function)
interface.c:367: error: (Each undeclared identifier is reported only once
interface.c:367: error: for each function it appears in.)
interface.c:372: error: &#8216;destroy&#8217; undeclared (first use in this function)
```interface.c does import <gtk/gtk.h>; what else might I be missing?  Are these handlers obsolete, by any chance?

EDIT: I'm sorry, this was a stupid question.  I'm supposed to define the callbacks...  I thought they were predefined.

Thanks!

---

### Post by kknd on 2009-04-09
Need more context information (the code itself) to see whats happening, but probabily you're tryingto connect a signal, and you need to pass "delete-event" (as a string, not as an identifier).

---

### Post by Jesdisciple on 2009-04-10
Nah, I had monkeyed some code which passed a delete_event callback and then stupidly deleted the callback's definition.  Weeks later as I came back to the project, I thought it was a predefined function.

Sorry!

---

