---
title: "Linker library order"
date: 2007-11-28
forum: Programming Talk
---

### Post by Zugzwang on 2007-11-28
Hi all,

can someone explain why the order of the libraries when linking is important? For example, for my program,

g++ [...] main main.o reader.o order.o [...] -lobj -lcudd -lepd -lmtr -lst -lutil

works but

g++ [...] main main.o reader.o order.o [...] -lobj -lepd -lmtr -lcudd -lst -lutil

doesn't. (Symbols from libcudd are used in libobj). According to my understanding of linkers, it shouldn't make any difference since symbols are resolved in some kind of global symbol table.

Thanks!

---

