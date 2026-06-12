---
title: "cblas: using cblas_dgemv in a loop"
date: 2011-03-31
forum: Programming Talk
---

### Post by velocitatus on 2011-03-31
I want to optimise a program that needs to perform thousands of matrix multiplications. I was told about cblas, so I installed it following this

[http://ubuntuforums.org/showthread.php?t=1325671&highlight=cblas](http://ubuntuforums.org/showthread.php?t=1325671&highlight=cblas)

When I changed my naive matrix multiplication by cblas_dgemv, some weirds results appeared. So I made a very simple c program to test what is wrong, where I just multiply one 3x3 matrix by a 3x1 vector, both full of 1's. That worked fine, the result is a 3x1 vector full of 3's.

The problem occurs when I put the call to cblas_dgemv inside a loop. The first iteration gives the correct result, but the second iteration gives the result multiplied by two, and the third by three...

So I have no idea of what is going on. Do I need to reset something at each iteration? Is there any error in the call to cblas? Is it a problem of my install?

Thanks for any input.

I currently use ubuntu 9.10 64, clapack-3.2.1, atlas 3.8.3

test program:
#include <stdlib.h>
#include <stdio.h>
#include <cblas.h>
int main(int argc, char **argv)
{
  int c1, c2;
  double t1[9], t2[3], t3[3];

  t1[0] = 1;
  t1[1] = 1;
  t1[2] = 1;
  t1[3] = 1;
  t1[4] = 1;
  t1[5] = 1;
  t1[6] = 1;
  t1[7] = 1;
  t1[8] = 1;

  for (c1 = 0; c1 < 3; c1++)
  {
    t2[0] = 1;
    t2[1] = 1;
    t2[2] = 1;
    cblas_dgemv(101, 111, 3, 3, 1, t1, 3, t2, 1, 1, t3, 1);
    for (c2 = 0; c2 < 3; c2++)
    {
      printf("t3[%i] = %f\n", c2, t3[c2]);
    }
  }
return(EXIT_SUCCESS);
}

results:
t3[0] = 3.000000
t3[1] = 3.000000
t3[2] = 3.000000

t3[0] = 6.000000
t3[1] = 6.000000
t3[2] = 6.000000

t3[0] = 9.000000
t3[1] = 9.000000
t3[2] = 9.000000

---

