---
title: "static link or multi-thread libs?"
date: 2009-01-15
forum: Programming Talk
---

### Post by jimi_hendrix on 2009-01-15
i just built boost (on windows :() and have a choice between the two libs i mentioned up top and a .dll...which do i use for common task and what is the purpose of each?

---

### Post by dwhitney67 on 2009-01-15
I am not sure what you are asking because I do not program under, much less use Windoze.

A DLL is similar to a shared-object library in Linux, and is not included in the application until runtime.  This minimizes the byte-size of the application, but makes it dependent on an external library, which may or may not be available on each system where the application is needed.

When statically linking a library with an application, the application no longer depends on an external file because the library is included within the application.  This makes the application more portable, yet increases the size of the application.

Now... comparing a DLL with a Multi-Threaded library is like comparing apples to oranges.  That's where you lost me with your thread title.

P.S.  Under Linux, I usually link with the -mt version of the boost libraries.  However, I am not sure if the "mt" stands for multi-threading or not.  I doubt it does since there's a libboost_thread-mt.so (and .a)... seems kinda silly to have "thread" in the name of the library and also include "mt".

---

