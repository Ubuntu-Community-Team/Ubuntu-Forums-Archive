---
title: "[SOLVED] KDE4 config troubles."
date: 2007-12-16
forum: Programming Talk
---

### Post by Vadi on 2007-12-16
Hello,

I'm having some problems with cmake. When I run ./configure, I get this error:

> vadi@vadi-laptop:~/kmuddy$ ./configure
./configure: line 2: kde4-config: command not found
-- Check for working C compiler: /usr/bin/gcc
-- Check for working C compiler: /usr/bin/gcc -- works
-- Check size of void*
-- Check size of void* - done
-- Check for working CXX compiler: /usr/bin/c++
-- Check for working CXX compiler: /usr/bin/c++ -- works
CMake Error: ERROR: Could not find KDE4 kde4-config
-- Configuring done
vadi@vadi-laptop:~/kmuddy$

I already installed the kdebase-dev-kde4 package and don't know what else to get.

---

### Post by lustefaniak on 2008-01-13
use 
```
export PATH=$PATH:/usr/lib/kde4/bin
```
and then try to compile. this helped me compiling yakuake

---

### Post by Vadi on 2008-01-13
Ah, sorry I forgot to post. Yes that's what solved it.

Or now, just installing kde4-devel does the trick.

---

### Post by b0n60 on 2008-09-27
thanx so much :D

export PATH=$PATH:/usr/lib/kde4/bin
and installing kde4-devel helped

---

