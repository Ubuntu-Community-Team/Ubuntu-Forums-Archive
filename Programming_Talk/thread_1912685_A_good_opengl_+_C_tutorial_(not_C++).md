---
title: "A good opengl + C tutorial? (not C++)"
date: 2012-01-21
forum: Programming Talk
---

### Post by SGFzc2U= on 2012-01-21
Hello, I have been searching for good modern opengl + C tutorials with google. Everything seems to involve C++ somehow. I do not want to learn a new programming language to do something that should be possible with C. I've tried to read many opengl + C++ tutorials and adapt them to C, but the problem comes when I need to do transformations. Then many tutorials link to GLM and force to switch to C++.

 I know i could just make the file from .c to .cpp but I think it's kind of stupid to write programs in C and then get some useless overhead from C++.

So I'm asking if you know a good C + opengl tutorial? (also I'd prefer them with SDL, but it's not necessary since adapting that is easy.)

---

### Post by Hetepeperfan on 2012-01-21
You could try: [http://www.lighthouse3d.com/tutorials/](http://www.lighthouse3d.com/tutorials/)

I don't know if it's really good though.
ohterwise try to get yourself a copy of the redbook

[http://www.opengl.org/documentation/red_book/](http://www.opengl.org/documentation/red_book/)

cheers,

Maarten

---

### Post by SGFzc2U= on 2012-01-21
That seems to be a very good tutorial. I have seen that site before, I just thought it's C++ only, but a closer inspection made it clear that it's C/C++. Thanks!  :D

---

### Post by Simian Man on 2012-01-22
> **SGFzc2U= said:**
> Hello, I have been searching for good modern opengl + C tutorials with google. Everything seems to involve C++ somehow. I do not want to learn a new programming language to do something that should be possible with C. I've tried to read many opengl + C++ tutorials and adapt them to C, but the problem comes when I need to do transformations. Then many tutorials link to GLM and force to switch to C++.
Even if you don't use C++, you should be able to understand code written in it.  Taking the OpenGL calls and incorporating them into a C program would be a good exercise that you understand them.  I would rather find good OpenGL tutorials that explain what's going on - even if the language is something you don't know.

> I know i could just make the file from .c to .cpp but I think it's kind of stupid to write programs in C and then get some useless overhead from C++.
There is no "overhead" of C++ if you do not use C++ features such as virtual functions or exceptions.

---

### Post by satsujinka on 2012-01-22
> **Simian Man said:**
> Even if you don't use C++, you should be able to understand code written in it.  Taking the OpenGL calls and incorporating them into a C program would be a good exercise that you understand them.  I would rather find good OpenGL tutorials that explain what's going on - even if the language is something you don't know.


There is no "overhead" of C++ if you do not use C++ features such as virtual functions or exceptions.
Yes and no...
Generally, C++ compilers do a slightly worse job than C compilers so C code is usually marginally faster... however, we're taking very small differences so effectively they have the same performance.
[http://shootout.alioth.debian.org/u32/cpp.php](http://shootout.alioth.debian.org/u32/cpp.php)

---

### Post by N1GHTS on 2012-01-23
This is what helped me get my feet wet. It teachings laid the framework for me to build an enterprise level OpenGL server software interface from scratch: 

[http://nehe.gamedev.net/](http://nehe.gamedev.net/)

It has examples in many software languages and for many platforms. Have fun!

---

