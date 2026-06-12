---
title: "open mp troubles"
date: 2009-06-18
forum: Programming Talk
---

### Post by burnt water on 2009-06-18
Why is only 1 thread active at a time in this function?

int isprime( mpz_t x )
{
    int i = 1;
    int h;
    mpz_t max;
    mpz_t mod;
    mpz_t loop;
    mpz_init_set_d( loop, 2 );
    mpz_init( mod );
    mpz_init( max );
    mpz_sqrt( max, x );
    mpz_mod( mod, x, loop );
    printf("\n%d  ", n );
    if( mpz_cmp_d( mod, 0 ) == 0 ) { //handles check for n=2;
        gmp_printf( "%Zd was not prime:", x );
        return 0;
    }
    mpz_set_ui( loop, 3 );
    omp_set_num_threads(threads);
    #pragma omp parallel
    {
        #pragma omp for schedule(dynamic,chunk) nowait

            for( h = 0; mpz_cmp( max, loop ) >= 0; mpz_add_ui( loop, loop, 2 ) ) {
                GPTLstart("prime");
                mpz_mod( mod, x, loop );
                if( mpz_cmp_d( mod, 0 ) == 0 ) {
                    gmp_printf( "%Zd was not prime:", x );
                    i = 0;
                    break;
                }
                GPTLstop("prime");
            }

    }

    return i;
}> 

---

### Post by MadCow108 on 2009-06-19
a for loop must have a single exit in openmp.
so you can't use break in the loop
actually it shouldn't even compile. Are you sure your compiling with -fopenmp?

also is the chunksize defined?
(and use code tags to post sourcecode)

---

