---
title: "declaring variables using gmp"
date: 2011-08-19
forum: Programming Talk
---

### Post by suryak on 2011-08-19
Hi!
language I'm dealing with is C.

There is a puzzle I trying to solve which needs to take very large values .. ( large that 'long long int / long double').
So, I was suggested to use gmp. well, I installed it but when I started reading documentation.. its very confusing...

To be very specific about my problem.

how do I declare variables in gmp for taking large values.
how do I print them.... 

just tell me how does arithmetic calculations goes with them.. same as usual or different.

Thanks

---

### Post by ziekfiguur on 2011-08-19
here is an example from the gmp manual with some added comments, it contains everything you should need to get you going.

[PHP]
#include <stdio.h>
#include <gmp.h>

void
foo (mpz_t result, const mpz_t param, unsigned long n)
{
    unsigned long i;
    mpz_mul_ui(result, param, n); // multiply `param' by unsigned integer `n' and store the result in `result'
    for (i = 1; i < n; i++)
        mpz_add_ui (result, result, i*7); // add unsigned integer `i * 7' to `result' and store the result in `result'
}

int
main (void)
{
    mpz_t r, n;  // mpz_t are gmp integers 
    mpz_init(r); // initialize the mpz_t variable `r' so it can be used
    mpz_init_set_str(n, "123456", 10); // initialize `n' and give it the value 123456 with base 10
    foo(r, n, 20L); // the result of the function will be stored in r
    gmp_printf("%Zd\n", r); // print `r' as a large integer
    return 0;
}
[/PHP]

---

