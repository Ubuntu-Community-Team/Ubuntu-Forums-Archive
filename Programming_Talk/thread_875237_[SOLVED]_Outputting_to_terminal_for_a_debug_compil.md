---
title: "[SOLVED] Outputting to terminal for a debug compile only?"
date: 2008-07-30
forum: Programming Talk
---

### Post by Zeotronic on 2008-07-30
C++: I'm working on a program and I decided the other day to include code to output information to terminal with which I could debug it. Specifically I want to know if there is a way to make the compiler ignore my code when I am not compiling a debug version, or short of that, a way to get my program to output essentially all of it's information to terminal in a way that is humanly legible, without adding a lot of new code.

---

### Post by dribeas on 2008-07-30
> **Zeotronic said:**
> C++: I'm working on a program and I decided the other day to include code to output information to terminal with which I could debug it. Specifically I want to know if there is a way to make the compiler ignore my code when I am not compiling a debug version, or short of that, a way to get my program to output essentially all of it's information to terminal in a way that is humanly legible, without adding a lot of new code.

Classic solution is through the use of macros, something in the line of:

```

#ifdef _DEBUG
// Either std::cout or printf would be fine.
#define DEBUG(x) std::cout << x << std::endl
#else
#define DEBUG(x)
#endif

```

But I would go for a logging library for any but the simplest problems. Logging libraries are quite easy to use and they allow you to log/ignore logs at runtime with just a small runtime penalty. I use [ACE]("http://www.cse.wustl.edu/~schmidt/ACE.html") for that (company decision), but I used before [log4cpp]("http://log4cpp.sourceforge.net/") and it was really flexible and powerful. You can look into [Boost]("http://www.boost.org") logging library (I don't know if it was yet approved into Boost, but it is quite good)

---

