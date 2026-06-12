---
title: "Compiled on Linux, Can run on windows?"
date: 2006-03-12
forum: Programming Talk
---

### Post by rab on 2006-03-12
I've searched this forum but found no answers. I wanna know if i compile my c++ code, will it be able to run on windows? Its just console programming.

---

### Post by pharcyde on 2006-03-12
If you compile a program on a linux platform and run the binary in windows it will not work.  The opposite is also true from windows compiled binaries moving to linux, although it is possible to run some using wine.

If your source code is fairly platform independent then you can probably recompile it under windows and have it work there.

---

### Post by skymt on 2006-03-12
Nope, sorry. Linux and Windows have entirely different executable formats. Interpreted languages like Ruby or Python would work fine, though.

---

### Post by Lord Illidan on 2006-03-12
Nope, it can't. If you want a decent c++ compiler for Windows, try Dev-C++

---

### Post by harisund on 2006-03-12
Exactly what sort of a code are you talking about? 

As an example, I write code in Windows XP and compile it using cygwin (would that still qualify as writing code in Windows?) 

By "console programming" what exactly do you have in mind? If you simply use standard STL classes typically your program would compile. of course, the binaries compiled on one platform wouldn't run on the other, but the source code should compile. 

but if you are using any libraries specially available in Windows, you might have to do a bit of rewriting.

---

### Post by toojays on 2006-03-12
By the way, the mingw* packages give you a compiler which runs on GNU/Linux and builds binaries which work on Windows.

---

