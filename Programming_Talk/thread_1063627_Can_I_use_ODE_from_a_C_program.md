---
title: "Can I use ODE from a C program?"
date: 2009-02-08
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2009-02-08
Yes or no?

I think ODE is written in C++.

---

### Post by Wybiral on 2009-02-08
Yes, it's internally written in C++, but the API uses a C interface: [http://www.ode.org/ode-latest-userguide.html#sec_4_4_0](http://www.ode.org/ode-latest-userguide.html#sec_4_4_0)

In fact, it also has a C++ interface that's built on top of the C one (which is an interface to the underlying C++ implementation), strange, eh?

But any library you intend to have bindings for in other languages and easily integrate into existing projects *should* have a C interface...

---

