---
title: "&quot;Tasking&quot; in C++"
date: 2009-09-01
forum: Programming Talk
---

### Post by shynthriir on 2009-09-01
Been working with ADA lately (because of work, not by choice) and was wondering if C++ had something similar to tasks in ADA.

---

### Post by johnl on 2009-09-01
Hi,

Not terribly familiar with ADA, but it sounds like 'tasking' is similar to multi-threading.

C/C++ do not have threads included in the standard library, but there are multiple libraries you can use to accomplish threading, such as POSIX threads (pthreads) or boost::threads.  If you are using C++ I would recommend boost::thread, while for C I would use pthreads (since boost is a c++ framework).

---

### Post by dribeas on 2009-09-01
... plus boost::thread is terribly close to the draft of the new standard, meaning that it will probably be the standard way of threading with c++ in the near future.

---

### Post by shynthriir on 2009-09-01
Thanks, you knew enough to answer my question. Threads came to mind, but wasn't sure because I've never delt with them.

---

