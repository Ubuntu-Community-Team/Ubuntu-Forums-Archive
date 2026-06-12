---
title: "Random double generator problem (C Programming)"
date: 2011-03-30
forum: Programming Talk
---

### Post by safarin on 2011-03-30
Hi,

I trying to make a very simple program to give a random value.
Then I got stuck, rand() function only give a random value in integer.
 
The random value must not in range of 0 to 1 but something more than that, example from 0 to 40 in double or floating point.

Do anybody have any idea, facing this problem or found any function in C that can solve my problem?

Thank you :)

---

### Post by johnl on 2011-03-30
Try something like this (untested):

```

#include <stdio.h>
#include <stdlib.h>

/* generate a random floating point number from min to max */
double randfrom(double min, double max) 
{
    double range = (max - min); 
    double div = RAND_MAX / range;
    return min + (rand() / div);
}

```

---

### Post by safarin on 2011-03-30
> **johnl said:**
> Try something like this (untested):

```

#include <stdio.h>
#include <stdlib.h>

/* generate a random floating point number from min to max */
double randfrom(double min, double max) 
{
    double range = (max - min); 
    double div = RAND_MAX / range;
    return min + (rand() / div);
}

```

Tested! Problem solved.
Thank you Johnl.

:popcorn:

---

