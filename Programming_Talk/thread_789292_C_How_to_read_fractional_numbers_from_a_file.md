---
title: "C: How to read fractional numbers from a file?"
date: 2008-05-10
forum: Programming Talk
---

### Post by fredscripts on 2008-05-10
Hi!!!

I'm trying to read a matrix from a file, the elements of the matrix are in the format:

1 1/2 1/3 1/4
1/2 1/3 1/4 1/5
1/3 1/4	1/5 1/6
1/4 1/5 1/6 1/7

I want to parse them as double with fscanf(..."%le",...) but they are evalued as integer division. How can I solve that?


Thank you very much!!!

---

### Post by SledgeHammer_999 on 2008-05-10
maybe read them as string(char*) and then cast the string into a double?

---

### Post by fredscripts on 2008-05-10
That will evaluate all that fractional numbers? I mean if I make something like asciitodouble(1/2) returns 0.5? Works like the eval(1/2) on python?

I thought there was any kind of %fractional to read from scanf fractional numbers...

Thank you very much!!

---

### Post by WW on 2008-05-10
> **SledgeHammer_999 said:**
> maybe read them as string(char*) and then cast the string into a double?
In C, you can't "cast a string into a double".

Assuming you can parse the file to get the numbers as separate strings, the function frac_to_double() in the following code can convert the fraction to a double.

**fractest.c**
```

#include <stdio.h>
#include <stdlib.h>
#include <string.h>


double frac_to_double(const char *s)
{
    char *p;
    double val;

    p = strchr(s,'/');
    if (p != NULL)
        val = atof(s)/atof(p+1);
    else
        val = atof(s);
    return val;
}

int main(int argc, char *argv[])
{
    char *f1, *f2;
    double v1,v2;

    f1 = "12/25";
    v1 = frac_to_double(f1);
    printf("%s = %f\n",f1,v1);
    f2 = "123";
    v2 = frac_to_double(f2);
    printf("%s = %f\n",f2,v2);
    return 0;
}

```

Compile and run:
```

$ gcc -Wall fractest.c -o fractest
$ ./fractest 
12/25 = 0.480000
123 = 123.000000
$ 

```

---

### Post by Replicon on 2008-05-10
I don't think there is such a thing. The %foo stuff is really meant for types, not fancy stuff that some other library (e.g. boost) should provide. If you're using plain C, you can always read it as a series of %s (assuming there will never be spaces within the terms of course), and parse them yourself.

Or, if your app doesn't require being in C, then why not juts do it in perl or ruby, where you DO have the ability to eval?

---

### Post by fredscripts on 2008-05-10
Thank you very much!!! I'm using pure C for a numerical computation on a math course!!! I'm gonna try the code you attached!!

---

