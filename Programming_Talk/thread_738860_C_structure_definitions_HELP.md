---
title: "C structure definitions HELP"
date: 2008-03-29
forum: Programming Talk
---

### Post by urangela on 2008-03-29
I am in the process of teaching myself C;
I wrote this tiny little program, and for some reason it won't compile:

#include <stdio.h>
struct B
{
	int X;
	int Y;
};

int main()

{
	B.X = 4;
	B.Y = 7;
	return 0;
}
When I compile, I get the following errors:

intswap2.c: In function ‘main’:
intswap2.c:14: error: ‘B’ undeclared (first use in this function)
intswap2.c:14: error: (Each undeclared identifier is reported only once
intswap2.c:14: error: for each function it appears in.)

I have tried moving the semicolon at the end of my struct definition arround, all over the place, but nothing. I am using what I presume is the latest version of gcc:
gcc (GCC) 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2).

which is what came up when I entered gcc --version into the shell.

I checked the syntax of my little program on a number of different websites / tutorials, and it looks correct. Any suggestions or advice is much appreciated.

PS everything is indented as it aught to be, it just doesn't look like it. Anjuta does it automatically.

---

### Post by PaulFr on 2008-03-29
Please see **[http://www.cs.princeton.edu/~lworthin/126/precepts/structs.html](http://www.cs.princeton.edu/~lworthin/126/precepts/structs.html)** for examples of **definition** and **declaration** of struct's in C. You have defined a struct, but not declared any variable of that type.

---

### Post by ruy_lopez on 2008-03-29
> **urangela said:**
> I am in the process of teaching myself C;
I wrote this tiny little program, and for some reason it won't compile:


You have defined the structure. But you still have to declare the structure, to set aside storage.
```

int main()
{
        struct B myB; /* can be any non-reserved name */

        myB.X = 4;
        myB.Y = 7;
        
        return 0;
}

```

---

### Post by urangela on 2008-03-31
AHHHHHHHHH, As I look at it i realize the sillieness of my error. Thank you guys! I feel kind of dumb, but more knowlegdeable now than yesterday ! great link Paul. I found the site to be quite informative.

---

### Post by rye_ on 2008-04-01
you may also want to look into using the preporcessor directive "typedef"

---

