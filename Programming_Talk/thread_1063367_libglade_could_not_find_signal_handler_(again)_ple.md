---
title: "libglade: could not find signal handler (again) please help"
date: 2009-02-07
forum: Programming Talk
---

### Post by mkarnicki on 2009-02-07
Why does libglade have problems connecting to signal handlers, if it looks like that:

---------
main.c:
#include some.h
...
glade_xml_auto_connect

---cut---

---------
some.h:
some_handler();
---cut---

---------
some.c:
#include some.h
some_handler()
{
//something useful
}
---cut---

I tried compiling with -Wl,-export-dynamic but it didn't help. I need to #include some.c instead of some.h for it to work, but it doesn't feel the right way to solve the problem.

---

