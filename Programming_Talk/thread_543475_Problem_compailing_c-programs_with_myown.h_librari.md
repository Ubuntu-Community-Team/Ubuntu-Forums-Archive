---
title: "Problem compailing c-programs with myown.h libraries?"
date: 2007-09-05
forum: Programming Talk
---

### Post by happogiri on 2007-09-05
I'm trying to compile (for learning purposes, in school) the following program:

```

/* main.c */
#include<stdio.h>
#include”first.h”
int main (void)
{
  first();
  return 0;
}

```

like this: ```
gcc -c main.c
```

first.h is:
```

/* first.h */

void first(void);

```

and first.c is like this:

```

/* first.c */
#include <stdio.h>
#include ”first.h”
void first (void)
{
  puts(” first ”);
}

```

When I try to compile, I get this error message:

main.c:3:10: error: #include expects "FILENAME" or <FILENAME>

I'm quite sure it has something to do with path but since I'm newbie in linux I can't seem to figure it out. I can include those standard libraries with <>, but my own "" it's problems. I've tried like this "./first.h"... :confused:

---

### Post by LaRoza on 2007-09-05
Compile with: ```
gcc main.c
```

OR
```

gcc -c main.c first.c
gcc main.o first.o -o binary

```
Line 0 compiles, line 1 links and makes an executable named "binary"

---

### Post by gnusci on 2007-09-05
Your code is completely correct, just try:

For compiling the object code and linking the executable:
```

$ gcc main.c first.c  -o main -I.

```

For only compiling object code:
```

$ gcc -c main.c first.c -I.

```

The option -I. tells to the compiler to look for includes in the actual directory, in case you want to use <first.h> instead "first.h".

---

### Post by Wybiral on 2007-09-05
It's best to compile the object files as shown by gnusci
```

gcc -c main.c first.c

```

Then link them like so
```

gcc main.o first.o -o my_program

```

Oh... And your error is because you need a space between '#include' and the file.

---

### Post by Compyx on 2007-09-05
> **Wybiral said:**
> 
Oh... And your error is because you need a space between '#include' and the file.

Not quite, it is allowed to have
```

#include"foo.h"

```
or
```

#include<bar.h>

```
without any whitespace.

The problem is the strange double-quotes, notice how they are tilted in the OP's code and not in this message?

---

### Post by nanotube on 2007-09-05
> **happogiri said:**
> I'm trying to compile (for learning purposes, in school) the following program:

```

/* main.c */
#include<stdio.h>
#include&#8221;first.h&#8221;
int main (void)
{
  first();
  return 0;
}

```


is it just me, or are those double quotes kinda weird-looking? try to delete them and retype them in directly (you probably copy-pasted from somewhere?)

edit: looks like compyx beat me to the punch. :)

---

### Post by happogiri on 2007-09-06
Thanks alot! It was the strange ""-marks...
What would I do without this forum? :)

I still can't compile the first.c, * warning: passing argument 1 of &#8216;puts&#8217; from incompatible pointer type* but I'll get into it.

---

### Post by gnusci on 2007-09-06
I also found out the problem with the double-quotes, so I did change all of them before to get your code compiled, so I advise you to change all the double-quotes inside all the source code, I also guess it is because you copy/paste it from a webpage, any I'm attaching the codes I use:

```

#include<stdio.h>
#include"first.h"
int main (void)
{
    first();
    return 0;
}

```

```

/* first.h */

void first(void);

```

```

/* first.c */
#include <stdio.h>
#include "first.h"
void first (void)
{
    puts("first");
}

```

You can compile it in one or two steps.
[COLOR="Red"]
One step:[/COLOR]

**$ gcc main.c first.c -o prog_exe**

[COLOR="Red"]Two steps:[/COLOR]

1) object code

**$ gcc -c main.c first.c**

2) binary code

**$ gcc main.o first.o -o prog_exe**

Now run your program with:

**$./prog_exe**

---

