---
title: "LibStd"
date: 2008-06-18
forum: Programming Talk
---

### Post by lexfridman on 2008-06-18
Hi,

I get the following Valgrind / GDB output when I run my code. This code works on Ubuntu 7.10 and not on 8.04. On 8.04 I get a seg fault with this output. Pasting my code is not a good option since there is a lot of it and the violating line provides no hints. Does this look familiar to anyone? It appears to be a problem in libstdc++.

```

==12458== 1 errors in context 1 of 2:
==12458== Invalid read of size 4
==12458==    at 0x687A561: std::string::size() const (basic_string.h:596)
==12458==    by 0x687D21B: std::string::assign(char const*, unsigned) (basic_string.tcc:267)
==12458==    by 0x80C1D52: main (main.cpp:19)
==12458==  Address 0xfffffff5 is not stack'd, malloc'd or (recently) free'd
==12458== 
==12458== 1 errors in context 2 of 2:
==12458== Use of uninitialised value of size 4
==12458==    at 0x687A561: std::string::size() const (basic_string.h:596)
==12458==    by 0x687D21B: std::string::assign(char const*, unsigned) (basic_string.tcc:267)
==12458==    by 0x80C1D52: main (main.cpp:19)

``````

```

---

