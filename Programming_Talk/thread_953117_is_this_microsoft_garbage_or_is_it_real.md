---
title: "is this microsoft garbage or is it real"
date: 2008-10-19
forum: Programming Talk
---

### Post by jimi_hendrix on 2008-10-19
im not on ubuntu all the time

whenever i need to do school work i have to use windows for printer compatability.  I also dont like to reboot much so i stay on windows afterwards.

i use the microsoft for C++ ide because it works for me and i dont mind the bloat

sometimes i see this parameter type LPWSTR (long pointer to a ??? string)  but on most tutorials and stuff where i get the function and i use their exact code (copy and paste) it wont compile because of this.

so two questions:

is this a real data type or microsoft im-going-to-ruin-your-code garbage?

how do i convert a string literal, char array, and string (data type) to this?

---

### Post by snova on 2008-10-19
It's Microsoft cruft. If I remember correctly, it's a Pointer to a Wide STRing.

Windows headers are full of this stuff.

---

### Post by dwhitney67 on 2008-10-19
It would break your code if you use it "unwisely".  Try to find from the M$ header files how that data type is defined, and then if you want, you can re-create the definition so that your code will compile under linux.

So for instance, LPWSTR referred to a char*, then something like this could be done:

[PHP]#ifdef WIN32
#include <stdafx.h>
...
#else                  
typedef char* LPWSTR;
...
#endif

// your code here[/PHP]

---

### Post by jimi_hendrix on 2008-10-19
and its totally inconsistant

i bought a book on game programming that used directX...the hoops i hade to jump through to get a simple message box to work *shudder* and im still stuck at about half way through because of M$ deciding to overhaul their compiler and give no support to other compilers

---

### Post by dwhitney67 on 2008-10-19
I'm sorry to read that you have to use M$ compilers.  Perhaps in the next life you will be more fortunate.

---

### Post by jimi_hendrix on 2008-10-19
> **dwhitney67 said:**
> I'm sorry to read that you have to use M$ compilers.  Perhaps in the next life you will be more fortunate.

i hope so

in heaven they use g++

---

### Post by Can+~ on 2008-10-19
How many Microsoft engineers you need to change a light bulb?

None. They just change the standard to darkness.

---

### Post by jimi_hendrix on 2008-10-19
how many programmers does it take to change a lightbulb?

answer:

1...then thousands to do it faster and with less CPU/RAM usage...

---

### Post by angustia on 2008-10-19
in many microsoft code you will see LP* like LPWSTR, LPCSTR, etc. LP stands for Long Pointer.

That's because once in the past windows was a 16 bits OS, and there was a transition between 16 bit and 32 bit code, and working with pointers in 16 bit code was very complex and dangerous and you have to keep clear where you were using a 16 bit pointer and where you were using 32 bits pointer (long pointer) because you can't mix them...

in linux you have something similar when crosscompiling code for x86 and x86_64, but this is more subtle because x86_64 is not so different from x86, compared to the difference between i286 and i386...


excuse my english

---

### Post by jimi_hendrix on 2008-10-19
ok so how do i convert a list of chars (c string) string (C++ string) or string litteral ("im a string litteral") to a LPWSTR

---

### Post by dribeas on 2008-10-20
> **jimi_hendrix said:**
> ok so how do i convert a list of chars (c string) string (C++ string) or string litteral ("im a string litteral") to a LPWSTR

Search MSDN and you'll find [this]("http://msdn.microsoft.com/en-us/library/87zae4a3(VS.80).aspx"). (Else just follow the link :))

Microsoft APIs are quite complex on how they handle strings, some of them are C style strings, some are C style with multibyte characters, some are pascal strings (size of string followed by contents)...

They have the problem of inheritance: they cannot change their APIs or else other software won't run, and then people won't buy new-windows as it does not run my-favorite-program (read this [column]("http://www.joelonsoftware.com/articles/fog0000000054.html") for some historical on backwards compatibility).

EDIT: Oh, just as a side note: Microsoft has not been the first or only one to develop their own versions of strings. Many frameworks do, take QT's QString as an example.

---

