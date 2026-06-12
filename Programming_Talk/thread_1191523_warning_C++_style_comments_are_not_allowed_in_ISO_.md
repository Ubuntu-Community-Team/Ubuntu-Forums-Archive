---
title: "warning: C++ style comments are not allowed in ISO C90"
date: 2009-06-19
forum: Programming Talk
---

### Post by leblancmeneses on 2009-06-19
it seems with -pedantic  flag part of CFLAGS makes 
gcc spit the following errors:

warning: C++ style comments are not allowed in ISO C90

so what types of comments are allowed if i cannot use: // or /*  */  style comments?

---

### Post by monraaf on 2009-06-19
Huh? These /* */ are valid C comment delimiters.

---

### Post by sujoy on 2009-06-19
C++ style comments not allowed refers to // not the /* */ pair

---

### Post by leblancmeneses on 2009-06-19
created small test project ...
// generates warning 
but
/* does not */


very interesting...

i wonder if -pedantic is worth the effort... seems i only get these warning in my project but nothing useful.

---

### Post by monkeyking on 2009-06-19
of course its worth the effort to use pedantic
just use
-std=c++98 or similar

---

### Post by nvteighen on 2009-06-19
Let's do some history :)

The **//** comments were created at BCPL, but during the development of its successor B, these were dropped in favor of **/* */**... and these were inherited by B's successor, C.

C++ decided to resurrected the BCPL-style comment, along with the C-style ones. Of course, these proved to be very handy for short comments and C compilers began to accept them as a non-standard feature. gcc, when using the default GNU89 "standard", will accept them... The issue is that -pedantic will switch compilation to ISO C90.

The newest C standard is C99 and accepts the BCPL/C++-style comments. Use **-std=c99** and it should work, even with -pedantic.

---

