---
title: "64bit vs 32bit precision gcc"
date: 2007-12-27
forum: Programming Talk
---

### Post by monkeyking on 2007-12-27
I'm having some issues with a program built for 32bit,
which have then been ported to 64bit.

There are some errors, which I've traced down to the internal precision.

Has anyone had similar problems and what was the solution.
Does anyone have an idea why this happens.


The program will offcause run with no problems, on 64bit systems if I use the -m32 compilerflag.

But since I have a need for the extra memory that 64 bit allows.
That is not a solution.

thanks in advance

---

### Post by samjh on 2007-12-27
More detail required.

What is the "internal precision" problem?  Can you give us use-cases of the problem and the offending code?

---

### Post by Wybiral on 2007-12-28
I agree with Samjh, there's no way of telling without seeing some code or knowing more. Can you try to isolate the problem? Have you used any debugging tools?

---

### Post by monkeyking on 2008-01-09
Sorry for not giving examples, but it took quite a few hours, maybe even days. tracking this one down.
I had been doing a program on a 32-bit ubuntu machine, that was working fine for months. But when I tried compiling it on a 64-bit ubuntu machine. The program began to throw random errors.

My program is using another program, which again in some far off, sence also depended on other programs, that lastly depended on the GNU scientific library..
The last code in this mail, is the full officiel gsl method for finding cubic roots.
[http://www.gnu.org/software/gsl/]("http://www.gnu.org/software/gsl/")

small example:
```

#include <stdio.h>
int main (void){
  float b, c;
  b = 1 / 3.0f;
  c = b * 3.0f - 1.0f;
  printf ("c: %.20f\n", c);
  return 0;
}

```
Compiling the above with for 32bit and 64bit yields.
```

gcc t.c -m32 -o t32
gcc t.c -o t64
./t32
c: 0.00000002980232238770
./t64
c: 0.00000000000000000000

```
So the problem can be quite obvious, but the solution is somewhat ackward.
I wonder how much of my programming that has to be thoroughly checked.

More info here [http://gcc.fyxm.net/summit/2003/Porting%20to%2064%20bit.pdf]("http://gcc.fyxm.net/summit/2003/Porting%20to%2064%20bit.pdf")
```

/* poly/solve_cubic.c
 * 
 * Copyright (C) 1996, 1997, 1998, 1999, 2000 Brian Gough
 * 
 * This program is free software; you can redistribute it and/or modify
 * it under the terms of the GNU General Public License as published by
 * the Free Software Foundation; either version 2 of the License, or (at
 * your option) any later version.
 * 
 * This program is distributed in the hope that it will be useful, but
 * WITHOUT ANY WARRANTY; without even the implied warranty of
 * MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU
 * General Public License for more details.
 * 
 * You should have received a copy of the GNU General Public License
 * along with this program; if not, write to the Free Software
 * Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA 02110-1301, USA.
 */

/* solve_cubic.c - finds the real roots of x^3 + a x^2 + b x + c = 0 */

#include <config.h>
#include <math.h>
#include <gsl/gsl_math.h>
#include <gsl/gsl_poly.h>

#define SWAP(a,b) do { double tmp = b ; b = a ; a = tmp ; } while(0)

int 
gsl_poly_solve_cubic (double a, double b, double c, 
                      double *x0, double *x1, double *x2)
{
  double q = (a * a - 3 * b);
  double r = (2 * a * a * a - 9 * a * b + 27 * c);

  double Q = q / 9;
  double R = r / 54;

  double Q3 = Q * Q * Q;
  double R2 = R * R;

  double CR2 = 729 * r * r;
  double CQ3 = 2916 * q * q * q;

  if (R == 0 && Q == 0)
    {
      *x0 = - a / 3 ;
      *x1 = - a / 3 ;
      *x2 = - a / 3 ;
      return 3 ;
    }
  else if (CR2 == CQ3) 
    {
      /* this test is actually R2 == Q3, written in a form suitable
         for exact computation with integers */

      /* Due to finite precision some double roots may be missed, and
         considered to be a pair of complex roots z = x +/- epsilon i
         close to the real axis. */

      double sqrtQ = sqrt (Q);

      if (R > 0)
        {
          *x0 = -2 * sqrtQ  - a / 3;
          *x1 = sqrtQ - a / 3;
          *x2 = sqrtQ - a / 3;
        }
      else
        {
          *x0 = - sqrtQ  - a / 3;
          *x1 = - sqrtQ - a / 3;
          *x2 = 2 * sqrtQ - a / 3;
        }
      return 3 ;
    }
  else if (CR2 < CQ3) /* equivalent to R2 < Q3 */
    {
      double sqrtQ = sqrt (Q);
      double sqrtQ3 = sqrtQ * sqrtQ * sqrtQ;
      double theta = acos (R / sqrtQ3);
      double norm = -2 * sqrtQ;
      *x0 = norm * cos (theta / 3) - a / 3;
      *x1 = norm * cos ((theta + 2.0 * M_PI) / 3) - a / 3;
      *x2 = norm * cos ((theta - 2.0 * M_PI) / 3) - a / 3;
      
      /* Sort *x0, *x1, *x2 into increasing order */

      if (*x0 > *x1)
        SWAP(*x0, *x1) ;
      
      if (*x1 > *x2)
        {
          SWAP(*x1, *x2) ;
          
          if (*x0 > *x1)
            SWAP(*x0, *x1) ;
        }
      
      return 3;
    }
  else
    {
      double sgnR = (R >= 0 ? 1 : -1);
      double A = -sgnR * pow (fabs (R) + sqrt (R2 - Q3), 1.0/3.0);
      double B = Q / A ;
      *x0 = A + B - a / 3;
      return 1;
    }
}

```

---

### Post by Zugzwang on 2008-01-09
Are you sure that your program really does not work as expected? Results of floating point instructions can be different on different architectures, this behaviour is perfectly normal. Requiring that a floating point result is precisely the value you expect is not the way to go, you should allow some minor deviations. 

But the results should be almost the same, up to some rounding errors. If that is not the case, then the algorithm you are using might me numerically unstable. See [http://en.wikipedia.org/wiki/Numerical_analysis]("http://en.wikipedia.org/wiki/Numerical_analysis") for details about numerical stability.

---

### Post by pmasiar on 2008-01-09
[What Every Computer Scientist Should Know About Floating-Point Arithmetic](http://docs.sun.com/source/806-3568/ncg_goldberg.html) : "floats are fuzzy around the edges and not "dense" enough"

Found at [http://learnpython.pbwiki.com/FloatTricks](http://learnpython.pbwiki.com/FloatTricks) (found for Python but arithmetics is the same)

---

### Post by monkeyking on 2008-01-09
Thanks for your replys.
Maybe I wasn't specific enough.

The problem isn't related to my part of the programming.
it's the GSL method, thats wrong.

The big problem is the 2. conditional. in the gsl routine.


This comparison doesn't use the generic gsl_is_equal procedure,
that chechs if 2 numbers are equal with a certain ridicilus tolerance like 1e-qazziiloin.

so for now, I've fixed my program, and 2 numbers are deemed equal  if the difference is smaller than an insane small value.

---

### Post by Zugzwang on 2008-01-10
Note that the problem of finding the **number of** roots is ill-conditioned by itself. An infinitely small deviation in the parameters of the cubic equation can make a difference whether there are two or three roots.

[http://en.wikipedia.org/wiki/Condition_number]("http://en.wikipedia.org/wiki/Condition_number")

---

