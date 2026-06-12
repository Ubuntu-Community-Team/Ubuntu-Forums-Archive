---
title: "controlling rand() in c"
date: 2008-10-31
forum: Programming Talk
---

### Post by jon zendatta on 2008-10-31
hell0..how can i manipulate this so output is always 6 different integers?cheers

```
for (m = 0; m < 6; ++m){  
   printf("%d\n", rand() % 40 + 1);
   }
```

---

### Post by samjh on 2008-11-01
Do you mean that you don't want more than one of the same number?

You could check whether it has already produced a number, and then skip to the next iteration if it has.

1. Make an array of six integers, initialise to 0.
2. Get random number x.
3. Loop through array to check if value of x exists.
3.1. If it doesn't, then store value of x into array.
3.2. If it does, then skip to step 2.
4. When array has been filled, print the values in the array.

---

### Post by jon zendatta on 2008-11-01
yes that is what i meant thanks.i'm a learner(obviously) but this seems a tedious way, having so many loops/comparisons! i was just thinking there must be a tidier way of expressing
while(x occurs only once)
   ;

---

### Post by samjh on 2008-11-01
C is a minimalist language.  The programmer is expected to do a lot of work himself.

It's a blessing and a curse: a blessing because the programmer knows exactly what is happening in his program, but a curse because it requires a programmer to know exactly what needs doing.  It's not a language which provides "automagic" ways to do things. :|

---

### Post by Nemooo on 2008-11-02
If you want different values from rand() you have to give it different seed each time it's called. Something that can be done using srand() and time(). Time will change constantly thus giving rand() a different starting seed each time it's called:

[php]#include <stdio.h>
#include <stdlib.h>
#include <time.h>

int main()
{
    int m;
    srand(time(NULL));
 
    for (m = 0; m < 6; ++m){  
        printf("%d\n", rand() % 40 + 1);

    return 0;
}[/php]

---

