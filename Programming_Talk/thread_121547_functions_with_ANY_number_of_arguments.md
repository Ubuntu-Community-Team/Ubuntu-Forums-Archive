---
title: "functions with ANY number of arguments"
date: 2006-01-25
forum: Programming Talk
---

### Post by glinsvad on 2006-01-25
Hi

I'm building my own class for string manupulations in C/C++ to refresh my programming skills a little (let's just say I used Win98 the last time I compiled anything :).

Basically I want to create my own sprintf, so I need to figure out how one declares a function that can accept ANY number of arguments of ANY type char/char*/int/float etc. Naturally function overloading is out of the question:
char* sprintf(char*,char);
char* sprintf(char*,char*);
char* sprintf(char*,int);
char* sprintf(char*,float);
char* sprintf(char*,char,char);
char* sprintf(char*,char,char*);
...

If I don't want to cast the information into a list of strings (char** like in main-funtion) before calling my sprintf, how can it be done? Or can't it?

Cheers

---

### Post by LordHunter317 on 2006-01-25
You use '...' in the argument declaration and the va_args macros in <stdargs.h>

---

### Post by glinsvad on 2006-01-25
Thanks man

Further info:
I googled stdarg.h (not stdarg*s*.h apparently...) and found a short description
[http://www.opengroup.org/onlinepubs/007908799/xsh/stdarg.h.html]("http://www.opengroup.org/onlinepubs/007908799/xsh/stdarg.h.html")

---

