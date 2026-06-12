---
title: "OpenMP parallelization"
date: 2012-08-07
forum: Programming Talk
---

### Post by hailholyghost on 2012-08-07
Hello,

I am trying to parallelize a program which adds a sequence of numbers.  The programs I'm writing here are trivial, but just meant to get the proper syntax so what I learn here can be used for a more meaningful program which is going to be a 13-for loop nest.

The serial version:
```
#include <stdio.h>
#include <stdlib.h>
#include <math.h>

int main (void) {
 double sum = 0.0;
 unsigned int i;
 double rad = 3.14159/180;
 for (i = 0; i <= 199939960; i++) {
    sum += pow(i,rad/4)/999999;
 }
 printf("Sum is %lf\n",sum);
 return 0;
}
```

It's almost as easy as "hello, world".

```
$ time ./serial
Sum is 216.385756

real    0m18.446s
user    0m18.390s
sys     0m0.002s
```

However, the parallelization does not work:
```
#include <stdio.h>
#include <stdlib.h>
#include <math.h>
#include <omp.h>

/*
int main (void) {
 double sum = 0.0;
 int i;
 double rad = 3.14159/180.0;
 omp_set_num_threads(2);
 #pragma omp parallel for\
   shared(sum,rad) private(i) schedule(static)
 for (i = 0; i <= 199939960; i++) {
    sum += pow(i,rad/4)/999999;
 }
 printf("Sum is %lf\n",sum);
 return 0;
}
*/

int main(void) {

double sum = 0.0;
int n, chunk, nthreads;
double rad = 3.14159/180.0;

omp_set_num_threads(4);
n = 199939960;
chunk = n/4;

#pragma omp parallel
{
  int tid, i;
  nthreads = omp_get_num_threads();
  tid = omp_get_thread_num();
  printf("my tid is %d\n", tid);

  for (i = chunk*tid; i <= chunk*(tid+1); i++) {
     #pragma omp critical
     sum += (pow(i, rad/4.0) / 999999.0);
  }
}

printf("Sum is %lf\n",sum);
return 0;

}

```My original attempt was commented out above.
And another attempt:
```

#include <stdio.h>
#include <stdlib.h>
#include <math.h>
#include <omp.h>

int main (void) {
 double sum = 0.0;
 unsigned int i;
 double rad = 3.14159/180;
 #pragma omp parallel shared(sum) private(i)
    for (i = 0; i <= 199939960; i++) {
       sum += pow(i,rad/4)/999999;
    }

 printf("Sum is %lf\n",sum);
 return 0;
}
```

How can I parallelize this for loop?  I've been looking at the tutorial here: [https://computing.llnl.gov/tutorials/openMP/#Directives](https://computing.llnl.gov/tutorials/openMP/#Directives) but I can't make much sense of it.

Any help or pointers are greatly appreciated :-)

---

### Post by slavik on 2012-08-07
There is only one sum, so only one thread can access it. Try creating a counting loop.

---

### Post by PaulM1985 on 2012-08-08
You could parallelise all of the pow() calls and perform the sum at the end.

To do this you would have something like:
```

int main (void) {
 double sumArry[199939960]
 double sum = 0.0;
 double rad = 3.14159/180;
 #pragma omp parallel for
    for (unsigned int i = 0; i <= 199939960; i++) {
       sumArry[i] = pow(i,rad/4)/999999;
    }

// Not parallel, just addition
    for ( unsigned int i = 0; i <= 199939960; i++) {
       sum += sumArry[i];
    }

 printf("Sum is %lf\n",sum);
 return 0;
}

```

So now all of the pow calls are done in parallel and the additions are all done on one thread.

Paul

EDIT: That array might be too large for your memory (762MB unless I have calculated incorrectly), so this might not work, just an idea.

---

### Post by hailholyghost on 2012-08-09
A colleague in the real world helped me out with this:

```
#include <stdio.h>
#include <stdlib.h>
#include <math.h>
#include <omp.h>

int main (void) {
 double sum = 0.0;
 double lsum = 0.0;
 unsigned int i;
 double rad = 3.14159/180;
 #pragma omp parallel private(lsum)
 {
    lsum = 0.0;
    #pragma omp for
    for (i = 0; i <= 199939960; i++) {
       lsum += pow(i,rad/4)/999999;
    }
    #pragma omp critical
    sum += lsum;
 }
 printf("Sum is %lf\n",sum);
 return 0;
}

```

This is the solution!

Thanks for your help slavik and PaulM1985!

---

### Post by MadCow108 on 2012-08-10
what you are doing is a so called reduction
openmp has builtin support for the basic ones like this one (summing):
[http://en.wikipedia.org/wiki/OpenMP#Reduction](http://en.wikipedia.org/wiki/OpenMP#Reduction)
[https://computing.llnl.gov/tutorials/openMP/#REDUCTION](https://computing.llnl.gov/tutorials/openMP/#REDUCTION)

---

