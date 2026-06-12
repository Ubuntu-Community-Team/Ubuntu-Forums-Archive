---
title: "Quick question in c?"
date: 2009-08-11
forum: Programming Talk
---

### Post by freakinjonathan on 2009-08-11
Hey I found this code on the internet and it does exactly what i need it to do except for the fact that it returns a whole number. It won't return like You took 1.5 second to spell your name. It would just say 1 sec. I don't know what "%.2lf" is. I know it is the variable but i have never seen it like that before. Thanks. 

```
/* difftime example */
#include <stdio.h>
#include <time.h>

int main ()
{
  time_t start,end;
  char szInput [256];
  double dif;

  time (&start);
  printf ("Please, enter your name: ");
  gets (szInput);
  time (&end);
  dif = difftime (end,start);
  printf ("Hi %s.\n", szInput);
  printf ("It took you %.2lf seconds to type your name.\n", dif );
 
  return 0;
}
```

---

### Post by neoAnderson on 2009-08-11
I think it's because the C time function returns a time_t object, which is always an integral value. So the number of seconds is the difference of two integrals which is also an integral. The %.2lf means provide 2 decimal places for the real number (floating point), but since the value is always integral it prints two '0's after the decimal.

---

### Post by pizmooz on 2009-08-11
time_t is in second-sized granules.

> 
It is almost universally expected to be an integral value representing the number of seconds elapsed since 00:00 hours, Jan 1, 1970 UTC. This is due to historical reasons, since it corresponds to a unix timestamp, but is widely implemented in C libraries across all platforms.


---

### Post by Mirge on 2009-08-11
I could be wrong, but I believe time_t is defined as a long int... though I read the C standard doesn't specify specifically what it should be, just an "arithmetic value".... someone please correct me if that's not right.

---

