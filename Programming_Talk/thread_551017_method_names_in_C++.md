---
title: "method names in C++"
date: 2007-09-14
forum: Programming Talk
---

### Post by Elisei on 2007-09-14
is there a way in C++ to return class & methods names like java does it: something like getClass().getMethod();

---

### Post by CptPicard on 2007-09-14
You're talking about "introspection" which is probably much harder to do in a non-virtual machine language than it is in Java. Personally haven't ever tried it, but [Google Is Your Friend]("http://www.google.fi/search?q=c%2B%2B+introspection&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:fi-FI:official&client=firefox-a") as always...

---

### Post by aks44 on 2007-09-14
C++ sucks at introspection (especially runtime introspection), unless you add tons of boiler-plate code. Just look at Microsoft's COM implementation to get an idea...

Compile-time instrospection is a bit better thanks to SFINAE but it's far from being useable anyway.

[Seal-Reflex]("http://seal-reflex.web.cern.ch") is a C++ instrospection library that you may want to check. No idea what it's really worth, never tried it since decent C++ code doesn't need introspection. (IMHO the need for introspection or even for "simple" dynamic_casts is just a sign of bad design, YMMV though)

---

### Post by pmasiar on 2007-09-14
Why do you need introspection is a statically typed language like C++? I would thing that dynamically typed languages are better suited for this kind of dynamic tasks. C++ does not have introspection for a reason...

---

### Post by dwhitney67 on 2007-09-14
Do a Google-search on RTTI (Run-Time Type Information) for C++.  It slightly kills performance, and is thus used infrequently by developers.

---

### Post by aks44 on 2007-09-14
> **pmasiar said:**
> C++ does not have introspection for a reason...

Because introspection is useless? :p

Just kidding ;) (oh well, not really kidding after all, when you think of it)


EDIT:
> **dwhitney67 said:**
> Do a Google-search on RTTI (Run-Time Type Information) for C++.

I guess you're thinking about the **typeid** operator?

If so, you should know that it only applies to classes, not methods. Moreover, neither type_info::name() nor type_info::raw_name() return anything consistent across different compilers (ie. the results are not portable).

dynamic_cast is hardly better, it can only allow you to test if an object is of a specific type (or derived from...).

---

### Post by pmasiar on 2007-09-15
> **aks44 said:**
> Because introspection is useless? .

Not useless, but it kills the performance. If you don't care about performance much, why even bother with C++? Do it in Python, you have introspection for free! :-)

> dynamic_cast is hardly better, it can only allow you to test if an object is of a specific type (or derived from...)

Yup, if you bother with that, go for the whole thing:  late type binding, "duck typing".

---

### Post by duff on 2007-09-15
..back to the original question...**if** you are using g++, and **if** you are inside the method you want the name of, and **if** you only need a string, you can use either "__FUNCTION__" or "__PRETTY_FUNCTION__".  __FUNCTION__ will just give you the method's name, __PRETTY_FUNCTION__ will give you virtual/static, return type, enclosing scope, method name, and formal parameter types (with templates instantiated).

Not much use, except for writing debugging macros.  For example, "assert" uses it.

---

