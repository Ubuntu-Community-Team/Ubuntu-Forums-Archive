---
title: "C++ weird behavior"
date: 2013-08-03
forum: Programming Talk
---

### Post by kangaba on 2013-08-03
Hi,
I have a class qgl in namespace mtl.
If I define the ctor/dtor in the header it compiles ok, if in the .cpp file it says while linking:
```
undefined reference to `vtable for mtl::qgl'
collect2: error: ld returned 1 exit status

```
if I define the ctor/dtor in both .h and .cpp files (that is twice to see what happens), it says "error: redefinition"
```

/media/docs/dev/Learn/mtl/qgl.cpp:13:1: error: redefinition of &#8216;mtl::qgl::qgl()&#8217;
In file included from /media/docs/dev/Learn/mtl/qgl.cpp:1:0:
/media/docs/dev/Learn/mtl/qgl.hpp:16:2: error: &#8216;mtl::qgl::qgl()&#8217; previously defined here
/media/docs/dev/Learn/mtl/qgl.cpp:17:1: error: redefinition of &#8216;mtl::qgl::~qgl()&#8217;
In file included from /media/docs/dev/Learn/mtl/qgl.cpp:1:0:
/media/docs/dev/Learn/mtl/qgl.hpp:18:10: error: &#8216;virtual mtl::qgl::~qgl()&#8217; previously defined here

```

Any ideas why it's so weird? That is, it find the ctor/dtor in the header file but in the .cpp file only in some cases.

---

### Post by trent.josephsen on 2013-08-03
> **kangaba said:**
> qgl
mtl
ctor/dtor

Ease off on the abbreviations, they make both your post and your code hard to understand.

I'll assume "constructor/destructor" for the last one, but that hardly helps since I don't know C++.

In C, you never define a (non-static, non-inline) function in a header file, because then you could get multiple copies at link time. Instead, you declare it in the header file and define it in only one source file, then link that object file to any other object files that need to use it. If you're having link problems, I'd guess it's related to the declaration in the header file being incomplete or incorrect in a way that affects the function's linkage. I know in C++ some member functions can be defined in header files (I guess they're usually inlined?), but that's as far as I'll go. If you post code for an example that gives the undefined reference error, I'm sure one of the resident C++ experts will be able to tell you what's wrong.

---

### Post by kangaba on 2013-08-03
Thanks, the problem was in the cmake file..

---

