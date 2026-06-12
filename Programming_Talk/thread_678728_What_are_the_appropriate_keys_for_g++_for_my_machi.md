---
title: "What are the appropriate keys for g++ for my machine?"
date: 2008-01-26
forum: Programming Talk
---

### Post by Zdravko on 2008-01-26
These are my g++ compiler keys, I use:
> 
CXXFLAGS := -ansi -std='c++98' -pedantic -Wall -Weffc++ -Wold-style-cast \
-Wextra -Wunknown-pragmas -Wshadow -Wwrite-strings -Wconversion \
-Wunreachable-code -Winline -Wdisabled-optimization -O3 -march=prescott \
-mfpmath=sse -mmmx -msse -msse2 -msse3
# link options
LDFLAGS := -s


I wonder, whether this is enough. My processor is Intel Pentium Dual-Core T2310.

---

### Post by Sockerdrickan on 2008-01-26
That's more than enough

---

### Post by Zdravko on 2008-08-09
It is never enough! I want more! :)

---

### Post by Zdravko on 2009-02-08
Anyone?

---

