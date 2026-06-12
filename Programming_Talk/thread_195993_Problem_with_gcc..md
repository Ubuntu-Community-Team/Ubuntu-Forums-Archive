---
title: "Problem with gcc."
date: 2006-06-13
forum: Programming Talk
---

### Post by chlag on 2006-06-13
Hello,
Well, I have a simple C program:
```
#include <stdio.h>
int x = 0;
main()
{
        while (x=!10) {
                printf("Hello world!\n");
                x++;
        }
        return 0;
}
```
The compilation of this program:
```
~$ gcc -o hello hello.c
```
went silently and without problem, but, if I do:
```
~$ ./hello
```
nothing happens.
What muste I do to execute this simple C program.
Thanks in advence for the answer.

---

### Post by bites on 2006-06-13
```
while (x=!10)
```

should be

```
while (x!=10)
```

just a small typo I guess ;)

Edit: '=!' assigns 10 to x, the result of the assignment is 1 (logically true) but it's negated by the '!' so the final result is 0.  This explains why the loop is never entered.  If you're new to C/C++, try compiling with the "-Wall" option.  This'll make GCC print some more warning messages!

---

### Post by chlag on 2006-06-13
Good morning,
ok! bites, it works perfectly since I changed ```
while (x=!10)
``` to ```
while (x!=10) 
```.
So, ./thanks
> //thanks.c
#include <stdio.h>
int x = 0;
main()
{
        while (x!=10) {
                printf("Thanks a lot!\n");
                x++;
        }
        return 0;
}

---

### Post by ynef on 2006-06-14
[QUOTE=bites]If you're new to C/C++, try compiling with the "-Wall" option.  This'll make GCC print some more warning messages![/QUOTE]
I find the "-pedantic" flag to be very useful too, since it complains about everything it can find. Installing a version of "lint" is very good as well (it checks your code for a variety of bad things) and if you ever run in to the message "Segmentation fault", "valgrind" is your new best friend...

---

