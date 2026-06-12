---
title: "[SOLVED] another simple c problem"
date: 2007-08-29
forum: Programming Talk
---

### Post by rbprogrammer on 2007-08-29
maybe today just isnt the best programming day, or maybe i'm just tired or whatever.. but i cant seem to see why this code does not work
```

#include <stdio.h>
#include <stdlib.h>
int main(int argc, char *argv[])
{
    int length = 3;
    float *numbers = (float*)malloc( length * sizeof(float) );
    float total = 0.0f;
    float average = 0.0f;
    int i = 0;

    for(i=0; i<length; i++)
    {
        printf("Please enter in a number for index %02i: ", (i+1));
        scanf("%f", &numbers[i]);
        total += numbers[ i ];
        printf("number: %f\n", numbers[i]);
        printf("total:  %f\n", total);
        printf("length: %d\n", length);
    }
    average = total / (float)length;
    printf("The Average is: %.2f\n\n", &average);
    free( numbers );
    return 0;
}

```
and then i compile, but i get errors:
```

$ gcc file.c
$ ./a.out
Please enter in a number for index 01: 5
number: 5.000000
total:  5.000000
length: 3
Please enter in a number for index 02: 10
number: 10.000000
total:  15.000000
length: 3
Please enter in a number for index 03: 15
number: 15.000000
total:  30.000000
length: 3
The Average is: 30.00

```
but if i were to comment out those printf()'s that were just used for debugging, i get
```

$ ./a.out
Please enter in a number for index 01: 5
Please enter in a number for index 02: 10
Please enter in a number for index 03: 15
The Average is: -0.33

```
clearly this program is just supposed to average a few numbers, and in this case, the average was supposed to be 10.

what's going on?

---

### Post by abadfish on 2007-08-29
> **rbprogrammer said:**
> 
    printf("The Average is: %.2f\n\n", **&**average);

Remove the ampersand.

---

### Post by samjh on 2007-08-29
Ah!  Beaten by 1 minute! ;)

Concur on the &.

---

### Post by rbprogrammer on 2007-08-29
yup, i feel so dumb asking these easy questions :( ..

its even worse when i know how to fix it, but i just cant see it at the moment..

thanks

---

### Post by abadfish on 2007-08-29
when in doubt, use the debugger.

---

### Post by rbprogrammer on 2007-08-29
> **abadfish said:**
> when in doubt, use the debugger.
true, just one problem for me.. i never learned how to use one yet.. maybe i should try to learn next time i have the time..

---

### Post by abadfish on 2007-08-29
you're using gnu tools, gdb is a very simple compiler to use and there are plenty of tutorials on the web and some decent man pages.  here's a suggestion..... keep your code with the bug in it and use gdb to step through it and various values at each line.  When you get to the line with the bug in it, you'll see that ampersand has the right value so the problem must be with the usage with printf().

---

### Post by LaRoza on 2007-08-29
> **abadfish said:**
> you're using gnu tools, gdb is a very simple compiler to use ...

Debugger

---

### Post by abadfish on 2007-08-29
oops, I stand corrected....gdb is a debugger.  That is also what I meant to say.

---

