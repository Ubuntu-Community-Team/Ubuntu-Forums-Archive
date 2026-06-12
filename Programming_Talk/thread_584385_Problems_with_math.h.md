---
title: "Problems with math.h"
date: 2007-10-20
forum: Programming Talk
---

### Post by russell.h on 2007-10-20
I'm trying to compile this program
```
#include<stdio.h>
#include<stdlib.h>
#include<math.h>

double x=0;
float y=0;
#include<stdio.h>
#include<stdlib.h>
#include<math.h>

double x=0;
float y=0;

unsigned long long in=0;
unsigned long long total=0;

int main()
{
        srand(time(0));

        for(total=1; total<=10000000; total++)
        {
                x= 2*(rand()/((double)RAND_MAX))-1;
                y= 2*(rand()/((double)RAND_MAX))-1;

                if(sqrt(x*x+y*y)<=1)
                {
                        in++;
                }
        }
        printf("Pi is approximately %f\n", 4*((double)in/(double)total));

        return 0;
}
```
It compiles and runs without errors on my Mac, but for some reason whenever I try to compile it on Ubuntu I get
```
/tmp/cc8jNRBK.o: In function `main':
pi.c:(.text+0x10f): undefined reference to `sqrt'
collect2: ld returned 1 exit status
```

Is there something wrong with math.h?

Thanks,

Russell

---

### Post by bruce89 on 2007-10-20
You have include -lm in the gcc command line.

---

### Post by russell.h on 2007-10-20
Update: Compiling with -lm makes it work. Am I supposed to have to do that?

---

### Post by gnusci on 2007-10-21
> **russell.h said:**
> Update: Compiling with -lm makes it work. Am I supposed to have to do that?

Yes, you have to, this means to the compiler yu are using **math** library, but in the case of the Mac can be that it is included by default.

---

