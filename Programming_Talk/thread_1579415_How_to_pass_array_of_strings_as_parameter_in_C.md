---
title: "How to pass array of strings as parameter in C"
date: 2010-09-21
forum: Programming Talk
---

### Post by bcz on 2010-09-21
Trying to get C code to handle the passing an array of 80 character strings to a subroutine

```

#include        <stdlib.h>
#include        <string.h>
#include        <stdio.h>

static int      i;
static char     r[5][81]; // pascal array [1..5] of string;

void sub(char *r[5][81]){
        fprintf(stdout,"%s\n",*r[2]);
        }

main(int argc, char **argv) {
        fprintf(stdout,"Program tto5 running\n");
        strncpy(r[2],"Test OK",80);
        sub(&r);
        fprintf(stdout,"Program tto5 exiting\n");
}

```

Note strings are NULL terminated, rather than length in byte 0.  Also by default  80 characters long

Any help appreciated

Rgds Bill

---

### Post by Bachstelze on 2010-09-21
Why are you making a pointer to the array? You don't need to, this works:

```
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

void sub(char r[5][81])
{
    printf("%s\n", r[2]);
}

int main(void)
{
    char r[5][81];
    strncpy(r[2], "Test.", 80);
    sub(r);
    return 0;
}

```

If for some reason you really want to use a pointer, you must add some parentheses:

```
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

void sub(char (*r)[5][81])
{
    printf("%s\n", (*r)[2]);
}

int main(void)
{
    char r[5][81];
    strncpy(r[2], "Test.", 80);
    sub(&r);
    return 0;
}

```

[font=monospace]char *foo[][/font] is an array of [font=monospace]char*[/font]s, [font=monospace]char (*foo)[][/font] is a pointer to an array of [font=monospace]char[/font]s.

---

### Post by bcz on 2010-09-22
Thanks for example code and explanation.  Just what I needed

The trivial code is simplified.  The subroutine needs to setup 3 arrays of strings, so seems I actually need a pointer

Rgds Bill

---

