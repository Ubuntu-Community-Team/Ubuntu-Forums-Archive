---
title: "Using tan(), sin() etc."
date: 2006-10-11
forum: Programming Talk
---

### Post by mavix on 2006-10-11
How do I use the tan() and sin() functions in GCC? I included math.h, but returns an error message.

---

### Post by Lord Illidan on 2006-10-11
I think you have to compile it with the -lm option.

like gcc foo.c -o foo -lm

---

### Post by MWAAAHAAA on 2006-10-11
If you ever wonder about how to use a function, try the manual page. For example 'man sin' gives me the following:

SIN(3)                     Linux Programmer&#8217;s Manual                    SIN(3)

NAME
       sin, sinf, sinl - sine function

SYNOPSIS
       #include <math.h>

       double sin(double x);
       float sinf(float x);
       long double sinl(long double x);

       Link with -lm.

Yada, yada, yada

---

### Post by 56phil on 2006-11-27
What do I need to install?
```

prh@phil-laptop:~$ man sin
No manual entry for sin

```

---

### Post by xtacocorex on 2006-11-27
You need to put std:: in front of sin, cos, and tan. That's if you didn't declare a namespace at the beginning of the code, which is not good practice if you are using more than one namespace in a code.

An example from my airfoil generation code:
[php]
PI=4.0*std::atan(1.0);
[/php]I did include cmath instead of math.h.
[php]
#include <cmath>
[/php]I didn't do any special linking in my compile and it works fine.

EDIT: Thought you were doing C++, so I don't know if cmath will work.

---

### Post by Choad on 2006-11-27
> **MWAAAHAAA said:**
> If you ever wonder about how to use a function, try the manual page. For example 'man sin' gives me the following:

SIN(3)                     Linux Programmer&#8217;s Manual                    SIN(3)

NAME
       sin, sinf, sinl - sine function

SYNOPSIS
       #include <math.h>

       double sin(double x);
       float sinf(float x);
       long double sinl(long double x);

       Link with -lm.

Yada, yada, yada
legend! i was wondering where the hell you find out about that stuff without just posting billions of threads on forums :rolleyes:

---

### Post by Ragazzo on 2006-11-28
> **56phil said:**
> What do I need to install?
```

prh@phil-laptop:~$ man sin
No manual entry for sin

```

manpages-dev

---

### Post by daniminas on 2006-11-28
Exist some basic guide or list of the parameters of Gcc?.. (then 'MAN')..

Thanks ;)

---

