---
title: "Undefined reference to log"
date: 2010-10-11
forum: Programming Talk
---

### Post by newport_j on 2010-10-11
When I compile my program, I get the following error:

/tmp/ccIkAqHW.o: In function `expon':
simlib.c:(.text+0x1370): undefined reference to `log'
collect2: ld returned 1 exit status

The relevant code is:

```

float expon(float mean, int stream) /* Exponential variate generation
                                       function. */
{
    return -mean * log(lcgrand(stream));

}


```


gcc compiler obviously does not like the log reference. How do I correct it?

Newport_j

---

### Post by Zugzwang on 2010-10-11
Make sure you include "<math.h>" in your program.

Then make sure you link against the mathematics library, i.e., the option "-lm" is passed to the linker.

---

