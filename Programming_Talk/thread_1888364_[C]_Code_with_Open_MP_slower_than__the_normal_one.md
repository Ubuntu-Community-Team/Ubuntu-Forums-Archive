---
title: "[C] Code with Open MP slower than  the normal one"
date: 2011-11-29
forum: Programming Talk
---

### Post by R33D3M33R on 2011-11-29
I have a dual core processor (AMD Athlon X2 4200+) and I would like to take advantage of the additional core. I discovered the Open MP library and wanted to do a simple test with it. So I wrote two big loops to test the single core speed. Then I divided the outer loop into two sections -> so each core can calculate one half. Suprisingly, the "two thread" code runs much slower that the original one. If I remove the lines that enable multi-core processing, the code executes as fast as with joined loop. So, what am I doing wrong?

```
#include <stdio.h>
#include <time.h>

void loop_nomp(int iter) {
  int i, j;
  double out;
  out=0.0;
  clock_t start = clock();
    for (i=0;i<=iter;i++) {
      for (j=0;j<=iter;j++) {
    out+=i*j;
    }
  }
  printf("%g\n",out);
  printf("Time elapsed: %f\n", ((double)clock() - start) / CLOCKS_PER_SEC);
}

void loop_mp(int iter) {
  int i,j,k,l;
  double outA,outB;
  outA=0.0;
  outB=0.0;
  clock_t start = clock();  
 #pragma omp parallel
 {
  #pragma omp sections nowait
  {
      #pragma omp section 
      {
      for(i=0;i<iter/2.0;i++) {
        for (j=0;j<=iter;j++) {
          outA+=i*j;
        }
      }
    }
     #pragma omp section 
     {
      for(k=iter/2.0;k<=iter;k++) {
        for (l=0;l<=iter;l++) {
          outB+=k*l;
        }
      }
      }
  }
 }
  printf("%g\n",outA+outB);
  printf("Time elapsed: %f\n", ((double)clock() - start) / CLOCKS_PER_SEC);  
}


int main() {

 loop_nomp(20000);
  loop_mp(20000);

return 0;
}
``````
gcc test.c -fopenmp
```
I'm using gcc version 4.4.5 (Debian 4.4.5-8)

---

### Post by San_SS! on 2011-11-29
I don't know exactly why it is not working better, but i see that you are using sections when OpenMP gives you more tools for paralleling for loops. You have "#pragma omp parallel for" for example, and in this case that you are adding you can use the reduction directive like this:

```

void loop_mp(int iter) {
        int i, out = 0;

        #pragma omp parallel for reduction(+: out)        
        for(i = 0; i < iter; i++){
           int j;
           for (j = 0; j < iter; j++) {
               out += i * j;
           }
        }
        printf("%d\n", out);
}

```

Try it, and see if this code runs faster than yours.

---

### Post by R33D3M33R on 2011-11-29
Thank you for your answer. Your code (with slight modifications) works as it should -> around twice as fast as the non-threaded loop. 

But the reason I used sections was to later use it with my real code. That code searches for the minimum through the loops. Something like this:

```

min[4] //array for storing indexes
float a,b,c,d //interval limits

for(i=0;i<=iter;i++) {
  x=function1(a,b,i)
    for(j=0;j<=iter;j++) {
    y=function2(c,d,j)
      u=function3(x,y)
      v=function4(x,y)
      ss=u*u+v*v
      if(ss < min[2]) {
         min[0]=x
         min[1]=y
         min[2] = ss
      }
   }
}

```The result is the array min.

I was thinking of finding the minimum for the first half of iter, and then for the second half. Lastly I would just compare them, and choose the smaller one.

---

### Post by San_SS! on 2011-11-29
To get the minimum I would do something like this, use a shared variable to get the global minimum and a local minimum for parallizing the search:

```

int minimum = 9999999;
#pragma omp parallel
{
  int local_min = 999999;
  #pragma omp for nowait
  for (int i = 0; i < iter; ++i) {
      if (array[i] < local_min)
          local_min = array[i];
  }
  #pragma omp critical
  {
     if (local_min < minimum)
         minimum = local_min;
  }
}

```

---

### Post by 3Miro on 2011-11-29
```
int minimum = 9999999;
```
is actually bad code. You are making the assumption that the minimum is less than 9999999 ~ 10 million, which is still way less than the 2.1 billion of the maximum signed integer. You should use:

```
int minimum = array[0];
#pragma omp parallel
{
  int local_min = array[0];
  #pragma omp for nowait
  for (int i = 1; i < iter; ++i) {
      if (array[i] < local_min)
          local_min = array[i];
  }
  #pragma omp critical
  {
     if (local_min < minimum)
         minimum = local_min;
  }
}
```

Maybe run a check to make sure iter isn't 0.

---

### Post by San_SS! on 2011-11-29
I put that as an example. I was making emphasis in how the parallel code should be and not in how the minimum is calculated. If you see he applies some functions to the array elements too.

---

### Post by R33D3M33R on 2011-11-29
Ok, so the for loop is divided between threads. Each thread calculates it's own minimum. At the end of the loop (critical section), the threads wait and compare their local minimum with the global minimum. Is this correct?

---

### Post by 3Miro on 2011-11-29
> **R33D3M33R said:**
> Ok, so the for loop is divided between threads. Each thread calculates it's own minimum. At the end of the loop (critical section), the threads wait and compare their local minimum with the global minimum. Is this correct?

Yes, that is the idea of the code.

---

### Post by R33D3M33R on 2011-11-29
Ok, I will try to implement it. Thank you both so far!

---

### Post by R33D3M33R on 2011-11-30
Although the implementation seems to work ok, there is still no speed gain/it works even a bit slower. I'm guessing the loop range (iter=100 => two 100 x 100 loops) is just too small to benefit from parallelization. I didn't realize the overhead from creating threads can impact the performance so much. Any other ideas or should I just forget about it?

---

### Post by 3Miro on 2011-11-30
> **R33D3M33R said:**
> Although the implementation seems to work ok, there is still no speed gain/it works even a bit slower. I'm guessing the loop range (iter=100 => two 100 x 100 loops) is just too small to benefit from parallelization. I didn't realize the overhead from creating threads can impact the performance so much. Any other ideas or should I just forget about it?

100x100 is incredibly small. At this level your code is probably spending more time loading into memory than actually running, then you get the extra load from just adding the OpenMP libraries. You need something more substantial to gain any real difference.

I do scientific simulations that take hours to complete, with the proper use of OpenMP I can do things like go from 5 hours down to 1. OpenMP is great, you just need a real problem to see its power.

---

### Post by 11jmb on 2011-11-30
> **R33D3M33R said:**
> Although the implementation seems to work ok, there is still no speed gain/it works even a bit slower. I'm guessing the loop range (iter=100 => two 100 x 100 loops) is just too small to benefit from parallelization. I didn't realize the overhead from creating threads can impact the performance so much. Any other ideas or should I just forget about it?

That is a safe bet. You could try, just for testing purposes, to crank up the number of iterations by factors of 10 and see if you get any speedup. 

Also, running on 2 processors will never be exactly twice as fast for many reasons, but your code looks alright, so the static overhead may just be more than the parallel speedup for such a small computation.

---

### Post by R33D3M33R on 2011-12-01
@3Miro: Yes, the loop seems small, but there are more outer loops and it adds up. This two loops are taking 98+ of the program calculating time to complete. That's why I thought I would give paralellization a try.

@11jmb: The loops were bigger initially, but it was so slow I had to take another approach. I change the interval limits according to the minimum I get, and put it back into the loops. I can even break out of the outer while loop if the minimum doesn't change and get even faster search.

---

### Post by 3Miro on 2011-12-01
> **R33D3M33R said:**
> @3Miro: Yes, the loop seems small, but there are more outer loops and it adds up. This two loops are taking 98+ of the program calculating time to complete. That's why I thought I would give paralellization a try.

@11jmb: The loops were bigger initially, but it was so slow I had to take another approach. I change the interval limits according to the minimum I get, and put it back into the loops. I can even break out of the outer while loop if the minimum doesn't change and get even faster search.

To get a better paralleled algorithm you should make the outer most loop parallel.
```

for( i=0; i<N; i++ ){
  for( j=0; j<M; j++ ){
  };
};

```
You should make the i look parallel and not the j loop (especially if the j loop is small).

If the j-loop is small, then you will gain no boost from OpenMP. In total you will have N * no-boost = no-boost.

If the j-loop is large, then you will gain some boost from OpenMP and in total you will have N * some-boost, but you will also pay the price to start parallel sections N times.

One way or the other, the i-loop is the largest that you have and you will only pay the price of starting one parallel section.

---

### Post by 11jmb on 2011-12-01
If there are more outer loops, you should parallelize those of you can. There is a static overhead incurred from branching and joining, so you will want to do as little of that as possible

---

### Post by R33D3M33R on 2011-12-02
I parallelized the most outer of the two loops. This are the largest loops in the program. Other loops tend to stop if a certain goal is achieved, so it will be probably not so smart to parallelize them.

---

### Post by 11jmb on 2011-12-02
> **R33D3M33R said:**
> I parallelized the most outer of the two loops. This are the largest loops in the program. Other loops tend to stop if a certain goal is achieved, so it will be probably not so smart to parallelize them.

That can often still be done in parallel if you are careful. 

My point was that parallelizing a loop as small as 100 iterations is not going to do much. Even if the short loop is called many times, that parallelization overhead will therefore happen every time. If you can parallelize the outermost loop, the fewest branches/joins will happen, and it will therefore have the greatest impact on your speedup

---

