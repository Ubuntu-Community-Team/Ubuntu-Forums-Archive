---
title: "Using C libraries in C++"
date: 2008-09-03
forum: Programming Talk
---

### Post by babyhuey on 2008-09-03
When programming in C++, can I use any C library in addition to C++ libraries or are there restrictions? I'm just curious, this isn't something I need to do atm. I just started using/learning C++. Most of my programming experience so far has been python and a bit of C#.

I just started my first computer science class(Structured Programming) at school which happens to use C++. So, no need for you python lovers to tell me not to learn C++ first =)

---

### Post by cabalas on 2008-09-03
To the best of my knowledge there isn't any limitations to using c libraries with c++.

---

### Post by cmay on 2008-09-03
yes . you can use the same libraries as in c with c++.
here is a link to a standard c/reference.
[http://cppreference.com/](http://cppreference.com/)

---

### Post by snova on 2008-09-03
The only catch is that all declarations of C functions must be prefixed with

```
extern "C"
```
Or else the compiler will mangle the names for C++, and you'll get strange link errors...

Most C libraries do this already. They'll use a macro at the top and at the bottom that expand to this:

```
extern "C" {
```
and

```
}
```
Which simply causes the effect to be applied to all declarations within.

None of this applies to variables, fortunately.

Oh, and although I do like Python for certain things, I support your decision (unless it isn't!) to learn C++ first. Starting with a lower level language has its benefits in that you learn more about the computer itself, and how it works, while you're at it.

It additionally gives you an appreciation for higher level languages. :)

---

