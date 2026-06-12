---
title: "How to test GMP without Boost?"
date: 2016-10-14
forum: Programming Talk
---

### Post by borucki-andrzej on 2016-10-14
I want test Gnu multi-precision library (GMP) without BOOST, low-lewel. After installing GMP is library libgmp.a and only one header gmp.h. No other headers like gmp-impl.h or longlong.h. But tests from directory tests of source distribution of GMP uses those headers.
1.I wanna GMP test which uses only gmp.h.
2.How test time of running with microsecond accuracy? In plain C, not C++, I must not use #include <chrono> ?

---

