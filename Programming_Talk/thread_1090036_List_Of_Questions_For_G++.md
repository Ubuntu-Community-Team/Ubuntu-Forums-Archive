---
title: "List Of Questions For G++"
date: 2009-03-07
forum: Programming Talk
---

### Post by ajm113 on 2009-03-07
I'm guesting most of these questions have been asked, but I would like to find out personally or if someone can throw me a link or 2 too answer my question(s) or give in detail. I can't install Ubuntu with Vista so its stuck on my PC until I turn it off.

1. Can G++ work with precompiled header(s)? Like all my includes for OpenGL/Fmod and so forth would be in one stdafx.h file. So all other files for my project would include that one stdafx so I wouldn't have to give a million includes to OpenGL?

2. How can I run libraries with my compile such as Fmod and SFML?

3. I have a performance handler using Window functions I need to convert to linux so my game can perform properly with fast or slow computers. 

Here are the functions needed to be converted:
QueryPerformanceCounter
timeGetTime

 3.1 What is the header(s) for the functions for Linux?


4. How can I deal with resource files with G++?

Thank you, Andrew. As you may guest I'm converting a game to Linux and I want to get this out of the way. Its not that I don't like Linux, but I don't see much of a need for it at the moment since most games run on Windows, if I have Vista already installed. But I'm sure one day I'll get ubuntu to keep.

---

### Post by cthug on 2009-03-07
Q4, do you windows gcc through cygwin or mingw?

---

### Post by ajm113 on 2009-03-07
No I used VS2008 on Windows. I think I mite have used G++ before, but never got too into it.

---

### Post by &#956; . on 2009-03-07
> **ajm113 said:**
> 
1. Can G++ work with precompiled header(s)? Like all my includes for OpenGL/Fmod and so forth would be in one stdafx.h file. So all other files for my project would include that one stdafx so I wouldn't have to give a million includes to OpenGL?

For the most part, yes but with some differences.
see: [http://gcc.gnu.org/onlinedocs/gcc/Precompiled-Headers.html](http://gcc.gnu.org/onlinedocs/gcc/Precompiled-Headers.html)

> **ajm113 said:**
> 
2. How can I run libraries with my compile such as Fmod and SFML?

[http://www.ibm.com/developerworks/linux/library/l-dynamic-libraries/](http://www.ibm.com/developerworks/linux/library/l-dynamic-libraries/)

> **ajm113 said:**
> 
3. I have a performance handler using Window functions I need to convert to linux so my game can perform properly with fast or slow computers. 

Here are the functions needed to be converted:
QueryPerformanceCounter
timeGetTime

3.1 What is the header(s) for the functions for Linux?

I'm not familiar those functions so I can't give you decent advice.
here's libc's manual though: [http://www.gnu.org/software/libc/manual/html_mono/libc.html](http://www.gnu.org/software/libc/manual/html_mono/libc.html)

> **ajm113 said:**
> 
4. How can I deal with resource files with G++?

I have no idea.

---

