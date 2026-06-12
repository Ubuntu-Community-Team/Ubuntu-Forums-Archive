---
title: "problems about using OpenMP in g++"
date: 2010-06-03
forum: Programming Talk
---

### Post by shengxingstars on 2010-06-03
Hi all,
 
I am trying to run a parallel OpenMP program in a multicore machine. The compile is successful. However, the program is not really "parallel", because all the threads are assigned to only one CPU, and all the other CPUs are idle. This is very inefficient. Can anyone help me out? Thanks!
 
The C++ source code is here:
 
# include <stdlib.h>
# include <stdio.h>
# include <omp.h>
 
int main ( int argc, char *argv[] )
{
  int id;
  double wtime;
  printf ( "\n" );
  printf ( "HELLO\n" );
  printf ( "  C/OpenMP version\n" );
  printf ( "\n" );
  printf ( "  Number of processors available = %d\n", omp_get_num_procs ( ) );
  printf ( "  Number of threads =              %d\n", omp_get_max_threads ( ) );
  wtime = omp_get_wtime ( );
  
#pragma omp num_threads(2);
# pragma omp parallel default(shared) private(id)
  {
    id = omp_get_thread_num ( );
 for (double i=1; i<1e5; i++) {printf ("  i = %f, i*i = %f\n", i, i*i);};
    printf ("  This is process %d\n", id );
  }
/*
  Finish up by measuring the elapsed time.
*/
  wtime = omp_get_wtime ( ) - wtime;
  printf ( "\n" );
  printf ( "HELLO\n" );
  printf ( "  Normal end of execution.\n" );
  printf ( "\n" );
  printf ( "  Elapsed wall clock time = %f\n", wtime );
  return 0;
}
 
 
Then compile: g++ -fopenmp hello.c

---

### Post by Zugzwang on 2010-06-03
Try not printing out the values in the main loop of your threads - As there can only be one thread accessing the "stdout" file at a time and most time of your program in spent there, this program cannot really benefit from multithreading.

---

### Post by shengxingstars on 2010-06-03
Thank you. So you are saying the program and compiler set up themselves are OK. If I just use my real calculation to replace the "printf" commands, will it benefit from the multithreading?
 
 
 
 
 
> **Zugzwang said:**
> Try not printing out the values in the main loop of your threads - As there can only be one thread accessing the "stdout" file at a time and most time of your program in spent there, this program cannot really benefit from multithreading.

---

### Post by Zugzwang on 2010-06-03
> **shengxingstars said:**
> Thank you. So you are saying the program and compiler set up themselves are OK. If I just use my real calculation to replace the "printf" commands, will it benefit from the multithreading?

I ran a test and replaced your computation kernel by:
```

{
  id = omp_get_thread_num ( );
  int j = 0;
  for (double i=1; i<1e10; i++) {j += i; };
  printf (" This is process %d\n", id );
}

```

On my computer, CPU load is ~180% when running this program. As this computer is dual-core, this looks fine.

---

