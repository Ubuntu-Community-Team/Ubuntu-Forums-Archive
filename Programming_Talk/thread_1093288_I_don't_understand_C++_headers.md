---
title: "I don't understand C++ headers"
date: 2009-03-11
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2009-03-11
I got some C code I have used in the past, and I want to use it with my first C++ project.

But when I try to compile, I get some weird errors "undefined reference to <C function>" about every C function I try to use.

And I did include headers for the C functions, and makefile has the C source files in it as well.

What's wrong? Does C++ need some namespaces and other crap to work?


Also, why there isn't .h or .hpp when including C++ standard things?

---

### Post by Simian Man on 2009-03-11
> **crazyfuturamanoob said:**
> I got some C code I have used in the past, and I want to use it with my first C++ project.

But when I try to compile, I get some weird errors "undefined reference to <C function>" about every C function I try to use.

And I did include headers for the C functions, and makefile has the C source files in it as well.

What's wrong? Does C++ need some namespaces and other crap to work?

That is *way* too vague.  There can be any number of things wrong.  Please give more info.  Also read [this excellent article]("http://www.gamedev.net/reference/articles/article1798.asp") on the topic.

> **crazyfuturamanoob said:**
> 
Also, why there isn't .h or .hpp when including C++ standard things?
Because that's what the standards committee decided.  I think it's dumb, but we're stuck with it.

---

### Post by stroyan on 2009-03-11
C++ does name mangling to implement types.  The names of functions and variables are actually remapped into an implementation dependent encoding of the types of the functions, function parameters, and variables.

To access plain C variables and functions you need to tell the C++ compiler that the declarations are not supposed to have C++ name mangling.  Most C headers in /usr/include have the following code in them to make them work with both C and C++.

```

#ifdef __cplusplus
extern "C" {
#endif

/* All of your C declarations go in here. */

#ifdef __cplusplus
}
#endif

```

---

### Post by crazyfuturamanoob on 2009-03-11
> **stroyan said:**
> C++ does name mangling to implement types.  The names of functions and variables are actually remapped into an implementation dependent encoding of the types of the functions, function parameters, and variables.

To access plain C variables and functions you need to tell the C++ compiler that the declarations are not supposed to have C++ name mangling.  Most C headers in /usr/include have the following code in them to make them work with both C and C++.

```

#ifdef __cplusplus
extern "C" {
#endif

/* All of your C declarations go in here. */

#ifdef __cplusplus
}
#endif

```

That's the problem. Thanks. :)

---

