---
title: "How to use C++ code in C"
date: 2006-06-13
forum: Programming Talk
---

### Post by bhubanmm on 2006-06-13
Hello,

I am trying to use a C++ library in a C program. I have to use this library as I did not find any equivalent library in C. I have developed half of my application in C and I can not revert back to C++. Can anyone please help me in implementing this.:?: 

Thanks in advance.

---

### Post by toojays on 2006-06-13
You will probably find that the C code you have written so far will actually compile under G++. So if you can build your project with g++ instead of gcc, then you can use C++ code wherever you need to.

Otherwise you will need to write a C wrapper around your C++ library.

By the way, what is the functionality you need? Maybe someone has an idea for you.

---

### Post by LordHunter317 on 2006-06-13
No, it isn't as simple as being able to compile everything in G++.

You'll have to write wrapper functions around all your C++ code and extern "C" them.    There are several ways to do this, the C++-FAQ-Lite online covers a few of them, I think.

---

### Post by mdurham on 2006-06-13
I think toojays is correct for using a C++ library, most C will compile without problems (famous last words!). 
Maybe LordHunter317 could explain what he means when he says "You'll have to write wrapper functions around all your C++ code and extern "C" them." What C++ code?

Cheers

---

