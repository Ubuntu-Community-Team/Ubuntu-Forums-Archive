---
title: "nested loop in c"
date: 2010-01-09
forum: Programming Talk
---

### Post by 1991sudarshan on 2010-01-09
could any one please explain me the mechanism of nested "for" loop inc language!!!!!

---

### Post by wmcbrine on 2010-01-09
Eh? There's no mechanism... just one "for" loop inside another. If you know how to do a single "for" loop, then you can just as easily do nested loops.

Or did you really mean something besides "nested loop"?

---

### Post by 1991sudarshan on 2010-01-09
does the loop control get shifted form first loop to second loop and then back to first loop or else the second loop is executed completly and then goes to the first loop ???

---

### Post by Queue29 on 2010-01-09
> **1991sudarshan said:**
> does the loop control get shifted form first loop to second loop and then back to first loop or else the second loop is executed completly and then goes to the first loop ???

The inner for-loop will be initiated the number of times the outer for loop executes.

---

### Post by 1991sudarshan on 2010-01-10
thank you for the answer!!!!

---

### Post by dwhitney67 on 2010-01-10
> **1991sudarshan said:**
> thank you for the answer!!!!

Why did you elect *not* to write a test program?

```

#include <stdio.h>

int main()
{
   int i, j;

   for (i = 0; i < 5; ++i)
   {
      printf("i loop is executing...\n");

      for (j = 0; j < 2; ++j)
      {
         printf("j loop is executing...\n");
      }
   }

   return 0;
}

```
Are you fearful of doing basic research on your own?

---

