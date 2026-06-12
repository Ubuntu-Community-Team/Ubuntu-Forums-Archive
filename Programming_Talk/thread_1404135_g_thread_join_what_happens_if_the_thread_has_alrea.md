---
title: "g_thread join: what happens if the thread has already quit?"
date: 2010-02-11
forum: Programming Talk
---

### Post by night_fox on 2010-02-11
Hi.

supposing i call g_thread_join on a thread. What is supposed to happen if the thread has already quit?

My program segfaults when it exits about 1 in 4 times, but when run in gdb it never segfaults. Valgrind crashes during creation of a thread. Is debugging this going to be hard?

---

### Post by night_fox on 2010-02-11
anyway it doesn't matter. Not sure what i did to it but now i can't get it to segfault ever.

---

