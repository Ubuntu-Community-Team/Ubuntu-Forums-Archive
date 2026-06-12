---
title: "OpenMP performance with heap arrays"
date: 2011-07-06
forum: Programming Talk
---

### Post by drlemon on 2011-07-06
Hello,

I am a fairly experienced OpenMP user, but I have just run into a puzzling problem, and I am hopeful that someone here could help.
Consider a very, very simple piece of code that uses a hash function i%M (i modulus M) to count every M-th integer in respective array element (for simplicity, imagine N=1000000, M=10).
```

#pragma omp for
  for (int i=0; i<N; i++) 
    bins[ i%M ]++;

```
Array bins[] is private to each thread (I sum results of all threads in a critical section afterwards). 
When bins[] is allocated on the stack, the program works great, with performance scaling proportionally to the number of cores.
However, if bins[] is on the heap (pointer to bins[] is on the stack), performance drops drastically. And that is a major problem!
I want parallelize binning (hashing) of certain data into heap arrays with OpenMP, and this is a major performance hit.
There seems no reason why good performance of OpenMP should be limited to stack arrays.

It is definitely not something silly like all threads trying to write into the same area of memory. 
That is because each thread has its own bins[] array, results are correct with both heap- and stack-allocated bins, and there is no difference in performance for single-thread runs.
I reproduced the problem on different hardware (Intel Xeon and AMD Opteron), with GCC and Intel C++ compilers. All tests were on Linux (Ubuntu and RedHat).

Any guesses? Maybe access of threads to the heap goes through some kind of shared gateway on Linux? How do I fix that? 

Complete program to play around with is below:
```

#include <stdio.h>
#include <omp.h>

int main(const int argc, const char* argv[])
{
  const int N=1024*1024*1024;
  const int M=4;
  double t1, t2;
  int checksum=0;
  
  printf("OpenMP threads: %d\n", omp_get_max_threads());

  /////////////////////////////////////////////////////////////////////////////////////////////////////
  // Case 1: stack-allocated array
  t1=omp_get_wtime();
  checksum=0;
#pragma omp parallel
  { // Each openmp thread should have a private copy of bins_thread_stack on the stack:
    int bins_thread_stack[M];
    for (int j=0; j<M; j++) bins_thread_stack[j]=0;
#pragma omp for
    for (int i=0; i<N; i++) 
      { // Accumulating every M-th number in respective array element
    const int j=i%M;
    bins_thread_stack[j]++;
      }
#pragma omp critical
    for (int j=0; j<M; j++) checksum+=bins_thread_stack[j];
  }
  t2=omp_get_wtime();
  printf("Time with stack private array: %12.3f sec, checksum=%d (must be %d).\n", t2-t1, checksum, N);
  /////////////////////////////////////////////////////////////////////////////////////////////////////



  /////////////////////////////////////////////////////////////////////////////////////////////////////
  // Case 2: heap-allocated array
  t1=omp_get_wtime();
  checksum=0;
#pragma omp parallel 
  { // Each openmp thread should have a private copy of bins_thread_heap on the heap:
    int* bins_thread_heap=(int*)malloc(sizeof(int)*M); 
    for (int j=0; j<M; j++) bins_thread_heap[j]=0;
#pragma omp for
    for (int i=0; i<N; i++) 
      { // Accumulating every M-th number in respective array element
    const int j=i%M;
    bins_thread_heap[j]++;
      }
#pragma omp critical
    for (int j=0; j<M; j++) checksum+=bins_thread_heap[j];
    free(bins_thread_heap);
  }
  t2=omp_get_wtime();
  printf("Time with heap  private array: %12.3f sec, checksum=%d (must be %d).\n", t2-t1, checksum, N);
  /////////////////////////////////////////////////////////////////////////////////////////////////////
  
  return 0;
}

```Sample outputs of the program for OMP_NUM_THREADS=1 and 10 are below:
```

OpenMP threads: 1
Time with stack private array:        2.973 sec, checksum=1073741824 (must be 1073741824).
Time with heap  private array:        3.091 sec, checksum=1073741824 (must be 1073741824).

``````

OpenMP threads: 10
Time with stack private array:        0.329 sec, checksum=1073741824 (must be 1073741824).
Time with heap  private array:        2.150 sec, checksum=1073741824 (must be 1073741824).

```I would very much appreciate any help!

---

### Post by slavik on 2011-07-07
maybe it's the extra lookup or possibly the threads are accessing the same piece of memory stored in l2/l3 cache and you get a cache sync issue.

---

### Post by drlemon on 2011-07-07
Thanks, slavik, that seems to be exactly what it was.
For other viewer's sake, here is a link to a detailed answer to this question I got on stackoverflow:
[http://stackoverflow.com/questions/6605677/openmp-poor-performance-of-heap-arrays-stack-arrays-work-fine](http://stackoverflow.com/questions/6605677/openmp-poor-performance-of-heap-arrays-stack-arrays-work-fine)

---

### Post by slavik on 2011-07-07
it was sort of a blind guess. but this type of issue is what we discussed in class when I was learning about parallel systems.

---

