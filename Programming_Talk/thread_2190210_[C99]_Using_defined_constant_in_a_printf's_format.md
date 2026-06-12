---
title: "[C99] Using defined constant in a printf's format"
date: 2013-11-26
forum: Programming Talk
---

### Post by ppplayer80 on 2013-11-26
Hi,

I was wondering if it is possible to use a defined constant, like
```
#define PRECISION 3
```
In a printf format, like
```
printf("%.PRECISIONf", SomeFloatVariable);
```

How to define a number's precision by a constant?

---

### Post by steeldriver on 2013-11-26
You can specify the precision as an extra *argument* using '*' instead of the actual width e.g.

```
printf("%.*****f\n", **PRECISION**, floatval);
```

There's a variant that allows you to use a numbered argument [COLOR=#0000ff]**[CORRECTED (I hope) - thanks Bachstelze!]**[/COLOR] e.g.

```
printf("%**[COLOR=#0000ff]1$[/COLOR]**.***4$**f %**[COLOR=#0000ff]2$[/COLOR]**.***5$**f %[COLOR=#0000ff]**3$**[/COLOR].***4$**f\n", floatval, floatval, floatval, **PRECISION**, **PRECISION_ALT**);
```

```

#include <stdio.h>

#define M_PI 3.14159265358979323846264338327

#define PRECISION 3
#define PRECISION_ALT 6

int main()
{
  printf("%.*f\n", PRECISION, M_PI);

  printf("%1$.*4$f %2$.*5$f %3$.*4$f\n", M_PI, M_PI, M_PI, PRECISION, PRECISION_ALT);

  return 0;
}

```

```

$ gcc -std=c99 -Wall -o prec prec.c
$ 
$ ./prec
3.142
3.142 3.141593 3.142
$ 

```

- see the printf man page (man 3 printf)

---

### Post by ofnuts on 2013-11-26
You can take advantage of the automatic abuttal of string constants if PRECISION is a string literal (which make this more suitable for whole formats):

```

#include <stdio.h>

#define FORMAT "%02x"

int main() {
    printf("The answer is : "FORMAT"\n",66);
}

```

But in most cases you should be using a precision parameter as indicated above.

---

### Post by Bachstelze on 2013-11-26
> **steeldriver said:**
> 
although this throws a "missing $ operand number in format [-Wformat]" warning for me it seems to work


I guess you should heed your own advice and read *man 3 printf*. ;) The *$* construct is not standard, and also, if you use it at all, then you should use it everywhere.

---

### Post by trent.josephsen on 2013-11-26
Another option
```
#define STRINGIZE(x) #x
#define PRECISION 3
...
printf("%." STRINGIZE(PRECISION) "f", some_double);
```

I'd normally prefer steeldriver's first suggestion though.

The %n$ thing isn't just nonstandard; it's uncommon, and most C programmers have probably never heard of it, which means that unless it buys you something serious in clarity or performance, it's probably not worth the maintenance cost.

---

### Post by ofnuts on 2013-11-27
The things this format buys you is multi-language support, if the format string is a message to the user. Depending on language the substituted elements may not appear in the same order in the sentence.

---

### Post by ppplayer80 on 2013-11-27
Big thanks to you guys, I almost get it now. I just don't understand that "dollar" part. The beginning of the **steeldriver**'s post seemed to solve my problem, but then this appeared:
```
printf("%1$.*4$f %2$.*5$f %3$.*4$f\n", M_PI, M_PI, M_PI, PRECISION, PRECISION_ALT);
```
Couldn't it be written in this way:
```
printf("%.*f %.*f %.*f\n", PRECISION, M_PI, PRECISION_ALT, M_PI, PRECISION, M_PI);
```
?
And, if we follow that dollar method, why isn't it in this way:
```
printf("%1$.*2$f %1$.*3$f %1$.*2$f\n", M_PI, PRECISION, PRECISION_ALT);
```
?

Also I wonder how that first one worked. For example:
```
%1$.*4$f
```
You give it first argument at the start, but it refers to the whole number to display not precision. A second "dollar" tells the precision but it's closer to the end of the format...
I'm not sure if you know what I mean. You can simply avoid that last question if you like :)

---

### Post by Bachstelze on 2013-11-27
> **ppplayer80 said:**
> Big thanks to you guys, I almost get it now. I just don't understand that "dollar" part. The beginning of the **steeldriver**'s post seemed to solve my problem, but then this appeared:
```
printf("%1$.*4$f %2$.*5$f %3$.*4$f\n", M_PI, M_PI, M_PI, PRECISION, PRECISION_ALT);
```
Couldn't it be written in this way:
```
printf("%.*f %.*f %.*f\n", PRECISION, M_PI, PRECISION_ALT, M_PI, PRECISION, M_PI);
```
?
And, if we follow that dollar method, why isn't it in this way:
```
printf("%1$.*2$f %1$.*3$f %1$.*2$f\n", M_PI, PRECISION, PRECISION_ALT);
```
?


All of those do the same thing. 

In general I will agree with trent.josephsen that the $ construct does more harm than good. It's one of those things that seem to have been invented only to make a hacker's life easier (the only place I have ever seen it used in practice is in format-string-based attacks).

---

