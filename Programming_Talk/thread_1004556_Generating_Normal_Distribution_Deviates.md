---
title: "Generating Normal Distribution Deviates"
date: 2008-12-07
forum: Programming Talk
---

### Post by turezky on 2008-12-07
Hey, Everyone :)
Does anyone possess a code which would help me to generate random numbers which are distributed **normally**.

Example:
```
 int randomNumber = NormalDistribution.Next(mean, variance);
```

The function takes two parameters: *mean* and *variance* (optionally *standart deviation*) and returns a *random number*.
I would appreciate your help very much!
As for language... Java would be the best option but if you have any other implementations (except some exotic ones, e.g brainf*ck) I'd be pleased to see them also.
Thanks in advance!

---

### Post by WW on 2008-12-07
In python, with scipy:
```

>>> from scipy.stats import norm
>>> norm.rvs(size=5,loc=0,scale=0.5)
array([-0.44018532,  1.05318381,  1.0794372 ,  0.52152627,  0.40720329])
>>> 

```
"loc" is the mean, and "scale" is the standard deviation. "size" is the number of samples.

---

### Post by WW on 2008-12-07
Or in C, using the GNU Scientific Library:

gen_rand.c
```

#include <stdio.h>
#include <gsl/gsl_rng.h>
#include <gsl/gsl_randist.h>

int main (void)
    {
    const gsl_rng_type * T;
    gsl_rng * r;

    int i, n = 10;
    double sigma = 0.25; 

    gsl_rng_env_setup();
    T = gsl_rng_default;
    r = gsl_rng_alloc (T);

    /*
     *  Print n random variates chosen from the gaussian distribution
     *  with mean zero and standard deviation sigma.
     */

    for (i = 0; i < n; i++) 
        {
        double x = gsl_ran_gaussian(r, sigma);
        printf (" %f", x);
        }
    printf ("\n");
    gsl_rng_free (r);
    return 0;
    }

```

Compile and run:
```

$ gcc gen_rand.c -lgsl -o gen_rand
$ ./gen_rand 
 0.033480 -0.022025 0.418602 0.183410 0.249381 -0.319376 -0.599179 -0.169820 -0.009773 0.223389
$ 

```
See the chapter on [Random Number Distributions](http://www.gnu.org/software/gsl/manual/html_node/Random-Number-Distributions.html) in the GSL docs for more information and examples.

---

### Post by Lux Perpetua on 2008-12-07
There's a standard way to generate normal deviates from uniform deviates using polar coordinates. You need two uniform deviates, but you get two normal deviates as a result, so it evens out. 

If your two uniform deviates are u and v:

1. Let t = 2*pi*u, r = sqrt(-2*log(v)).
2. Let x = r*cos(t), y = r*sin(t).

Then x and y are your two standard normal deviates (mean 0, standard deviation 1). In general, if you want mean m and standard deviation s, return m + s*x, m + s*y instead of x, y. 

As for getting uniform deviates, best case: your standard library offers a facility to generate random numbers uniformly distributed between 0 and 1. I know this is often not the case; in this case, you should generate a random positive integer and divide the result by RAND_MAX or the equivalent. (Actually, the best case is that your standard library offers normal deviates, since it is likely to be faster than the above method. :-))

---

