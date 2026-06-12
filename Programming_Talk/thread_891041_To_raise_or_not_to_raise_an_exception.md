---
title: "To raise or not to raise an exception"
date: 2008-08-15
forum: Programming Talk
---

### Post by Erdaron on 2008-08-15
I started working on a library (again - personal use and learning experience, I imagine other people have done the same thing and better) to deal with 3D vectors.

I decided that a good format would be a list [float, float, float, str] where the last str variable specifies to what coordinate system the vector belongs (spherical, cartesian, etc.).

But then I came across this problem - how rigorously should I check data passed to the library to make sure it's in the correct format?

As an added challenge, I wanted to catch errors, if possible, in the library, so I could pass the exception back with a helpful message as to what went wrong.

Pretty much every function checks to make sure that coordinate types match, because otherwise this would be a silent error, using something like this (library is in Python):

[PHP]    if v1[3] != v2[3]:
        raise TypeError, 'Coordinate systems do not match.'[/PHP]

The tradeoff, it seems, is that if I rigorously check every vector to make sure it's in the right format, that would really slow down performance.

I also thought of using the try statement to execute various vector-vector operations, and if something goes wrong, use except clause to send offending vectors to an examining function.

So I guess I'm soliciting advice on how much care should I take, and how much freedom I should leave the programmer to screw up on his own.

---

### Post by txcrackers on 2008-08-15
A lot of it depends on what happens if the vectors aren't right. If the operation fails, is the error "meaningful"? That's usually the criteria I use...

---

### Post by slavik on 2008-08-15
add(int, int) should error out (using the language's standard error reporting routines, whether an exception or some other mechanism) if it is not given an (int, int).

---

### Post by Erdaron on 2008-08-15
> **txcrackers said:**
> A lot of it depends on what happens if the vectors aren't right. If the operation fails, is the error "meaningful"? That's usually the criteria I use...

I think the likeliest mistake would be to have a vector of incorrect length (2D instead of 3D). This would fail because v[3] does not exist, and it would error out on "list index out of range," or something like that. That could be misleading, perhaps.

The more I think about, I realize that I couldn't possibly predict all the ways that the input could go wrong.

---

### Post by lisati on 2008-08-15
I suspect that part of the answer is deciding how much could be detected at compile time, (e.g. a C/C++ compiler detecting the wrong number/type of arguments based on definitions in a header file somewhere), and how much could be detected at run time but with the extra overhead of some kind of sanity check.

---

### Post by hod139 on 2008-08-16
You can also do the error checking in a debug mode, and remove the runtime checking in a release mode.  For one example, assertions are turned off if the flag -DNDEBUG is passed to the compiler at compilation.
```

#ifndef NDEBUG
#define assert(THETEST) ...
#else
#define assert(THETEST) ((void)0)
#endif

```

This way you get the error checking when in debug mode, and no performance to error checks in release mode.

---

### Post by txcrackers on 2008-08-16
Sure, you can go the debug route, but I believe Erdaron's intent is to create a library - where he cannot guarantee the user's of said library will use it properly. And, no, you **can't** cover every possible erroneous input. You really only have two options:

[LIST=1]
[*]Cover the obvious/easy ones that you *know* will make things barf (e.g. vectors not the same dimensions).
[*]Catch everything and wrap it in one of yours.
[/LIST]

I usually go for #1 because #2 can be misleading and, if not properly wrapped, all semantics as to what the error **really** was is lost.

---

### Post by Reiger on 2008-08-16
> **Erdaron said:**
> The tradeoff, it seems, is that if I rigorously check every vector to make sure it's in the right format, that would really slow down performance.

I also thought of using the try statement to execute various vector-vector operations, and if something goes wrong, use except clause to send offending vectors to an examining function.

So I guess I'm soliciting advice on how much care should I take, and how much freedom I should leave the programmer to screw up on his own.

I am pretty much uneducated in the misteries of Python; still: can't you impose these constraints explicitly by requiring the functions be passed an 3d-Vector match-object (of your own design) instead of seperate vectors? Then, only when the object is instantiated do you require to check for the proper argument types; the functions merely extract those from an already valid object. ;)

---

