---
title: "Linking C++ Static Libs"
date: 2012-03-18
forum: Programming Talk
---

### Post by phylene on 2012-03-18
Could use some direction here; I have a static lib I've created using the correct tools; I know this as I have a working example test case. The only difference is the simple lib's syms are exported using extern and linked to a plain c prog. The actual use case is a c++ lib linked to a c++ program, so I've not wrapped the apis in extern braces. I've linked the calling app to the lib like this;

g++ -Wall -I../lib/include  -static -L../lib -lliblib  test.cc   -o test

and I get a plethora of undefined symbols. Output of nm 

nm -guA liblib.a yields nada.

nm liblib.a | grep Func gets me

0000000000000000 W _ZN10lib13Func4typeEPKc
0000000000000000 W _ZN10lib13FuncEPKc
0000000000000040 T _ZN10lib13Func5flushEv
0000000000000000 W _ZN10lib13FuncEPKc
(...)

So the methods I'm interested are getting exported, and the name mangled polymorphic exports seem ok, but ld can't seem to get its glue on. What else should I be looking at? Should I just go ahead and wrap the methods for unmangled C export as in my test case, even though its a c++ to C++ link?

Thanks to any and all.

---

### Post by dwhitney67 on 2012-03-18
> **phylene said:**
> 
g++ -Wall -I../lib/include  -static -L../lib -lliblib  test.cc   -o test


What's the name of your library?  Is it libliblib.a, or is it liblib.a?  If the latter, then your command above is incorrect.  Try:
```

g++ -Wall -I../lib/include  -static -L../lib -llib  test.cc   -o test

```

If you still are having trouble building your application, then please offer some more details as to a) what source code did you use for the library and b) how you built the library.

P.S.  I would recommend that you name your library lib[something].a, where the [something] is not "lib".

---

### Post by phylene on 2012-03-18
I'm not at liberty to actually name names. The code is named "somthing.cc", the library is named "something.a", resulting in a name of "libsomething.a", I don't believe theres an issue with the name. If it was a name problem the linker wouldn't tell me it can't find the symbols, it would simply say it can't find the lib, no? There's something I'm not doing in either the build or the linking, Seems like it could be a name mangling issue, but this is a c++ app to a c++ lib, I didn't think that would be an issue. Guess I'll go through the pain of using a C wrapper just as a sanity check.

---

### Post by phylene on 2012-03-19
Oh, I see how I confused you. the -lliblib thing. Its getting passed in correctly. It should read -llib. In any case, the previous post should explain why that's not an issue. Sorry for confusing the situation.

---

### Post by dwhitney67 on 2012-03-19
> **phylene said:**
> I'm not at liberty to actually name names. The code is named "somthing.cc", the library is named "something.a", resulting in a name of "libsomething.a", I don't believe theres an issue with the name. If it was a name problem the linker wouldn't tell me it can't find the symbols, it would simply say it can't find the lib, no? There's something I'm not doing in either the build or the linking, Seems like it could be a name mangling issue, but this is a c++ app to a c++ lib, I didn't think that would be an issue. Guess I'll go through the pain of using a C wrapper just as a sanity check.

From your first post, it seems that you are dealing only with C++.  Thus C wrapper stuff, albeit a necessary effort for certain libraries, may not be needed in your case.

I've thrown together a simple project (which I've attached) in which a static library is built with two types of functions: 1) inside a class definition, and 2) a free-floating.  The project demonstrates that each of these are callable by an application.

I would suggest that you look at this project to see if you had missed any steps in building your project.

Let me know if you have further questions.


P.S. To build the project:

```

1.  Download tar-ball

2.  Un-tar using this command:

        $ tar xvf StaticLibTest.tar

3.  Goto project directory:

        $ cd StaticLibTest

4.  Build and run it:

        $ make

```

Library source code is located in libsrc; application source code is located in appsrc.  There is a Makefile in each of these sub-directories, and another at the root-level of the project.

---

### Post by phylene on 2012-03-19
Thank you. I'll try it as soon as I can.

---

