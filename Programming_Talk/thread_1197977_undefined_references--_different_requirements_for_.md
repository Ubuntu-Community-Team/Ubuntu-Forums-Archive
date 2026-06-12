---
title: "undefined references-- different requirements for static and dynamic libraries?"
date: 2009-06-26
forum: Programming Talk
---

### Post by stair314 on 2009-06-26
Say that I want to link foo.cpp against a library bar. I've found that if I declare a function myFunc() in bar but don't define it, I can use bar.a as long as foo.cpp doesn't call myFunc(), but if I try to use bar.so I will get an undefined reference error.
Is this because there is a requirement that dynamic libraries define all the functions they declare and no such requirement for static libraries, or have I botched something else up?
The reason I am doing this is that some of the functions in bar are based on CUDA and I want it to be possible to compile on the cpp part of bar on machines that don't have CUDA.

---

### Post by wojox on 2009-06-26
Undefined references occur in programs when a program tries to access a variable that has not previously been declared.

---

### Post by stair314 on 2009-06-26
That's neither an answer to my question nor, technically, true.

---

### Post by monraaf on 2009-06-26
> **stair314 said:**
> The reason I am doing this is that some of the functions in bar are based on CUDA and I want it to be possible to compile on the cpp part of bar on machines that don't have CUDA.

Use dlopen and dlsym for that.

---

### Post by stair314 on 2009-06-26
Thanks for the advice. I'm hoping to keep it cross-platform though. Unfortunately, other people who use the library are silly enough to use Windows.

---

