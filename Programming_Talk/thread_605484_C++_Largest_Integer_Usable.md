---
title: "C++ Largest Integer Usable"
date: 2007-11-07
forum: Programming Talk
---

### Post by TreeFinger on 2007-11-07
I am doing some Project Euler problems in C++. I am on one where you must find the largest prime factor of a very big number. that number being: 	 317584931803.

when compiling in Dev-C++ I get an error.
"integer constant is too large for "long" type "


the constant being the very large number.

---

### Post by CptPicard on 2007-11-07
Yeah, long is 4 bytes... use a "long long". Also, we had this issue in a thread a few days back; stick "LLU" at the end of your constant, so that it's "long long unsigned"...

---

### Post by PaulFr on 2007-11-07
See **/usr/include/limits.h** for the limits for the various integer types.

---

