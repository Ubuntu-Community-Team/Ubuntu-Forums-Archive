---
title: "Strange OpenMP issue"
date: 2012-07-27
forum: Programming Talk
---

### Post by hailholyghost on 2012-07-27
Hello,

I am working on trying to learn parallel programming.  I have a C program which works greatly one 1 processor.

When I try to run it in parallel, however, it does not give me the correct answers.  The program is 1402 lines long, so I don't feel it is appropriate to post the entire thing here, but it repeats this segment many times:

```
 FILE *f2;
 f2 = fopen("02","r");
 double d2err[S-200];
 if (f2 != NULL) {
    i = 0.0;
    double d2[S];
    while (!feof(f2)) {
       if (fscanf(f2,"%s %lf",&t,&d) != 2) {
          continue;
       }
       d2[i] = pow(d,-6.0);
       i++;
    }
    fclose(f2);
    for (i = 200; i < S; i++) {
       unsigned short int k = i-200;
       double sum = 0.0;
       for (j = i-200; j <= i; j++) { 
          sum += d2[j]/200; 
       }
       double mean = pow(sum,-1/6.0);
       if ((mean >= lowdistances[0]) && (mean <= hidistances[0])) {
          score[k]++;
          d2err[k] = 0.0;
       } else if (mean < lowdistances[0]) {
          d2err[k] = mean-lowdistances[0];
       } else if (mean > hidistances[0]) {
          d2err[k] = mean-hidistances[0];
       }
    }
 }
```

If I include

```
#include <omp.h>
```
and
```
omp_set_num_threads(4);
```

The program gives totally different results, even though I don't set any of the loops to be parallelized.

Does anyone know why the program would do this?  This might be a shared variable issue, but I don't know how to solve it.  The parallel activity shouldn't even be taking place but it is changing the code.

I'm a chemist, not a programmer, so please forgive any noob-ish errors;)

Much appreciated!

---

### Post by PaulM1985 on 2012-07-27
Do you have:
```

    #pragma omp parallel

```
anywhere?

If it repeats that segment often, have you thought about putting it in a function?  And maybe add some useful comments?

Paul

---

### Post by hailholyghost on 2012-07-27
Hi Paul,

the code ```
#pragma omp parallel
```

is not located anywhere in the program, and yet it still changes the results.  When I remove ```
omp_set_num_threads(4);
``` the program works fine, and when the threads are set again, the program no longer works, even without the #pragma.

I'm totally lost.  There may be some obscure issue I'm missing.  This contradicts the manual I've been reading.

-DC

---

### Post by PaulM1985 on 2012-07-27
This definitely seems odd.  Have you tried putting in:
```

            printf_s("%d\n", omp_get_num_threads( ));

```
at various points in the code to see if it has actually kicked off some threads that you don't know about?

If you are getting prints saying num threads is greater than one, something must have started somewhere.

Paul

---

### Post by hailholyghost on 2012-07-27
Hi Paul,

Just a side note that printf_s didn't compile, but printf did work:

```
printf("%d\n", omp_get_num_threads( ));
```

It returns 1 thread.

---

