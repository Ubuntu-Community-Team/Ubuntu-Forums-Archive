---
title: "problems compiling ruby"
date: 2007-03-20
forum: Packaging and Compiling Programs
---

### Post by rpm13 on 2007-03-20
I am using edgy which comes with ruby 1.8.4.  I need to use 1.8.5.
So I tried to compile it from sources.
I find that for example zlib, readline etc dont work.
Went into the ext/zlib directory and found that mkmf.log contains things like

```

have_library: checking for deflateReset() in -lz... -------------------- yes

"gcc -o conftest -I../.. -I../../. -I../.././ext/zlib  -g -O2 conftest.c  -L'../..'  -rdynamic -Wl,-export-dynamic     -lruby-static -lz  -ldl -lcrypt -lm   -lc"
conftest.c: In function `t'
conftest.c:3: error: `deflateReset' undeclared (first use in this function)
conftest.c:3: error: (Each undeclared identifier is reported only once
conftest.c:3: error: for each function it appears in.)
checked program was:
/* begin */
1: /*top*/
2: int main() { return 0; }
3: int t() { void ((*volatile p)()); p = (void ((*)()))deflateReset; return 0; }
/* end */

```

Note that Ive got zlib and zlib1g installed that put files like zlib.h and zconf.h in /usr/include

---

