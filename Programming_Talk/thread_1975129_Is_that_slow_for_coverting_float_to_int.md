---
title: "Is that slow for coverting float to int ?"
date: 2012-05-07
forum: Programming Talk
---

### Post by DaviesX on 2012-05-07
I have seen a tip that said the standard type convertion of float to in is slow, is that true for gcc ?
If so, how slow it will be ?

They said this code can make the convertion become faster.
```

#include <stdio.h>
#include <time.h>


inline int FLoatToInt ( float fNumber )
{
    int ival = *(int *)&fNumber;

    int mantissa = (ival & 0x07fffff) | 0x800000;
    int exponent = 150 - ((ival >> 23) & 0xff);

    if (exponent < 0)
        return mantissa << -exponent;
    else
        return mantissa >> exponent;
}


int main()
{
    int begin = clock ();

    float i;
    int integer;
    for ( i = 0; i < 100000.0f; i ++ )
    {
        for ( float j = i; j < i + 1.0f; j += 0.01 )
        {
            integer = FLoatToInt ( j );
            // integer = (int)j;
        }
    }

    int end = clock ();

    printf ( "%d %d", (int)integer, end - begin );

    return 0;
}

```

if it is faster, why doesn't someone who made compiler use this method ? Is there any downside using the code ?:)

---

### Post by Bachstelze on 2012-05-07
> **DaviesX said:**
> I have seen a tip that said the standard type convertion of float to in is slow, is that true for gcc ?

Where? From whom? How old? CPUs have an instruction to do that nowadays, I highly doubt anything you could tinker up would be faster than that.

---

### Post by DaviesX on 2012-05-07
It's from here, 
[http://stereopsis.com/sree/fpu2006.html](http://stereopsis.com/sree/fpu2006.html)

---

### Post by DaviesX on 2012-05-07
Thanks, You're right :), when I change the test code like this, the standard conversion is obviously faster than any method, after I turned on -march=prescott (Intel Pentium 4 Prescott which support MMX SSE, SSE2, SSE3 instruction set)

The result is: 
standard:             18000 (10000 for loop)
so-call fast way:  27000 (10000 for loop)

```

#include <stdio.h>
#include <time.h>


inline int FLoatToInt ( float fNumber )
{
    int ival = *(int *)&fNumber;

    int mantissa = (ival & 0x07fffff) | 0x800000;
    int exponent = 150 - ((ival >> 23) & 0xff);

    if (exponent < 0)
        return mantissa << -exponent;
    else
        return mantissa >> exponent;
}


int main()
{
    int begin = clock ();

    float i;
    int integer;

    for ( i = 0; i < 10000000.0f; i ++ )
    {
        integer = FLoatToInt ( i );
        integer = (int)i;
    }

    int end = clock ();

    printf ( "%d %d", (int)integer, end - begin );

    return 0;
}

```

---

### Post by cgroza on 2012-05-07
Still, I seriously doubt that you will ever need to optimize a type conversion...

---

