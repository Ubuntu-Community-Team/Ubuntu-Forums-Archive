---
title: "Check if a file or function exist, how? c++"
date: 2006-01-18
forum: Programming Talk
---

### Post by bartbes on 2006-01-18
I have a program written in c++ and I want to inlcude a file if it exists. Currently I am using this code:

#include <fstream>

ifstream backdoorh ( "backdoor.h" );

if ( !backdoorh.is_open() ) {
}
else {
include "backdoor.h "
}

But I get this compilation errors:

aangifte.h:5: fout: expected unqualified-id before ‘if’
aangifte.h:8: fout: expected unqualified-id before ‘else’

What is wrong?:confused:  Or does someone knows how to check if a function exists?

---

### Post by adwait on 2006-01-18
with
#ifdef

eg:
#ifdef somefun
#include<something>
#else
#include<something else>

I think.......

---

### Post by LordHunter317 on 2006-01-18
If that's your actual code, it's invalid.  You can't have a conditional in a function.

Moreover, you can't do conditional preprocessing like that, if that's what you're trying to do.  You should probably explain what you're trying to do, first.

---

### Post by jerome bettis on 2006-01-19
for any type of filesystem operations in C++, your best bet is too look at the boost libraries.  a few minutes googling for boost filesystem should give you the exact code you need.

---

### Post by LordHunter317 on 2006-01-19
[QUOTE=jerome bettis]for any type of filesystem operations in C++, your best bet is too look at the boost libraries.  a few minutes googling for boost filesystem should give you the exact code you need.[/QUOTE]I think he's trying to conditional preprocessing based on the existance of a file, which boost can't help him with.

---

### Post by jerome bettis on 2006-01-19
yeah not sure what is going on here ....  are you using makefile?

---

### Post by thumper on 2006-01-19
How about the makefile checking for the existance of the file and setting a compilation flag then use #ifdef 
```
#ifdef BACKDOOR_EXISTS
#include <backdoor.h>
#endif
```
GNU make is quite good at this type of thing.

But to answer your original question - like LordHunter317 said - the preprocessor (the bit that handles the #includes) isn't designed to work that way.

---

### Post by bartbes on 2006-01-19
I am using an Makefile but creating now I'm trying to create a .patch file

---

### Post by Lews Therin on 2006-01-20
You appear to be completely misunderstanding the preprocessor. It runs before you compile your program, not at runtime.

---

### Post by bartbes on 2006-01-23
[QUOTE=Lews Therin]You appear to be completely misunderstanding the preprocessor. It runs before you compile your program, not at runtime.[/QUOTE]
That's what I realised...

---

