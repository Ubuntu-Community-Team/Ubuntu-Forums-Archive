---
title: "C and Unicode Support !"
date: 2009-01-19
forum: Programming Talk
---

### Post by e_abdullah on 2009-01-19
Hi, all

First, this is the first post for me and I hope I will find the good answer. However, I have been working in a specific project with C language and I need it to be a platform-independent and portable and for this reason I need to ask about wchar_t data type.

Does it supported directly within gcc without any preprocessor conditions ?

if the answer is (No), Do I need to use (unsigned short) as a alternative solution ?

Note : I am a windows programmer but now I intend to understand POSIX OS by using Ubuntu (Grate OS) and I don't have enough background about the nature of gcc, but I have good experience about programming.

Best wishes,

Abdullah

---

### Post by snova on 2009-01-19
[http://en.wikipedia.org/wiki/Wide_character](http://en.wikipedia.org/wiki/Wide_character)

It is standard, though probably not what you're looking for (Unicode wise).

> It is not the same thing as Unicode.

> "The width of wchar_t is compiler-specific and can be as small as 8 bits. Consequently, programs that need to be portable across any C or C++ compiler should not use wchar_t for storing Unicode text. The wchar_t type is intended for storing compiler-defined wide characters, which may be Unicode characters in some compilers."

---

### Post by wmcbrine on 2009-01-19
That statement is slightly outdated. wchar_t was officially defined as Unicode in C99, IIRC. It still might be either 16 or 32 bits, though -- but not 8.

---

