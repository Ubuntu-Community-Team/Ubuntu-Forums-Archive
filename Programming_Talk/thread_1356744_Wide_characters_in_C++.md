---
title: "Wide characters in C++"
date: 2009-12-16
forum: Programming Talk
---

### Post by SunSpyda on 2009-12-16
when using the wcout and wcerr streams, GCC claims they don't exist in the std namespace. Is this just a non-ISO library, or am i doing something wrong?

---

### Post by Physical Hook on 2009-12-16
Works just fine on 4.4.1.

---

### Post by SunSpyda on 2009-12-16
Ah, mine is 3.4.5. That's probably why it doesn't work. That's what came with Code::Blocks though... why are they using one so out of date?

---

### Post by TheBuzzSaw on 2009-12-16
> **SunSpyda said:**
> Ah, mine is 3.4.5. That's probably why it doesn't work. That's what came with Code::Blocks though... why are they using one so out of date?

Code::Blocks has not been updated in quite some time. I have made it a habit to download Code::Blocks without MinGW, and I go fetch the latest MinGW myself (in Windows of course). As for dev inside Ubuntu, you should just have the latest g++. :P

---

