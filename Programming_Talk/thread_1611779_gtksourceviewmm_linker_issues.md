---
title: "gtksourceviewmm linker issues"
date: 2010-11-02
forum: Programming Talk
---

### Post by Stormqueen1990 on 2010-11-02
Hey there,
I'm having issues for linking a program using gtksourceviewmm library. I've searched on Google, and I've found this [thread]("http://ubuntuforums.org/showthread.php?p=6022730"), but the solution didn't work out for me :(
My g++ line is ```
g++ -o `pkg-config gtkmm-2.4 --cflags --libs gtksourceviewmm-2.0`
``` but I'm still getting the following error: ```
error: &#8216;gtksourceviewmm&#8217; has not been declared
```
Any ideas of what should I do?
I'm including this library as ```
#include <gtksourceviewmm.h>
```
Is this wrong?

Would appreciate any help.

Kind regards.

---

### Post by gmargo on 2010-11-02
It sounds more like a syntax error in your code, not a linking issue.  Try separating the compile and link steps.  (i.e. compile to a .o file, then link that)

---

