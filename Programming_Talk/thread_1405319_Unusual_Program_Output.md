---
title: "Unusual Program Output"
date: 2010-02-12
forum: Programming Talk
---

### Post by newport_j on 2010-02-12
Something seems to be seriously amiss here and I cannot find it.
I run the following code:

```

#include <iostream>
#include <cuda.h>
#include "sys/time.h"

__global__ void vecMult_d(int *A, int *B, int N)
{    
    int i = blockIdx.x * blockDim.x + threadIdx.x;
    if(i<N) { B[i]=A[i]*2; } 
}

void vecMult_h(int *A, int*B, int N)
{
   for(int i=0;i<N;i++) { B[i] = A[i]*2; }
}

int main()  {
   int  *a_h, *b_h;   //pointers to host memory; aka CPU 
   int  *a_d, *b_d;   //pointers to device memory, aka GPU
   int block_size,grid_size,n=501,ncounter,ncount=100,repcounter,repcount=100,time_d_start,time_d_end,time_h_start,time_h_end,time_d_slice,time_h_slice;
   struct timeval t1_start,t1_end,t2_start,t2_end;
   double time_dev_avg, time_host_avg, time_d[repcount], time_h[repcount], time_d_sum, time_h_sum;

// Start a LOOP for many trials of matrix classes
   for (ncounter = 0; ncounter<ncount; ncounter++)
   {
   n = 501 + 500*ncounter, time_d_sum = 0; time_h_sum = 0;




for (repcounter = 0; repcounter<repcount; repcounter++)
{

// allocate arrays on host
   a_h = (int *)malloc(sizeof(int)*n);
   b_h = (int *)malloc(sizeof(int)*n);   

// allocate arrays on device
   cudaMalloc((void **)&a_d,n*sizeof(int));
   cudaMalloc((void **)&b_d,n*sizeof(int));
   block_size = 64;
   grid_size = (int) ((n-1)/block_size)+1;

   for(int j=0;j<n;j++) a_h[j]=j; 


// GPU
   cudaMemcpy(a_d, a_h, n*sizeof(int),cudaMemcpyHostToDevice);
   gettimeofday(&t1_start,0);
   vecMult_d<<<grid_size,block_size>>>(a_d,b_d,n);
   cudaThreadSynchronize();
   gettimeofday(&t1_end,0); 
   cudaMemcpy(b_h,b_d,n*sizeof(int),cudaMemcpyDeviceToHost);


// CPU
   gettimeofday(&t2_start,0);
   vecMult_h(a_h,b_h,n);
   gettimeofday(&t2_end,0);

   time_d[repcounter] = (t1_end.tv_sec-t1_start.tv_sec)*1000000 + t1_end.tv_usec - t1_start.tv_usec; 
   time_d_start = t1_start.tv_sec*100000 + t1_start.tv_usec;
   time_d_end   = t1_end.tv_sec*1000000 + t1_end.tv_usec;
   time_d_slice = time_d_end - time_d_start;

   time_h[repcounter] = (t2_end.tv_sec-t2_start.tv_sec)*1000000 + t2_end.tv_usec - t2_start.tv_usec; 
   time_h_start = t2_start.tv_sec*100000 + t2_start.tv_usec;
   time_h_end   = t2_end.tv_sec*1000000 + t2_end.tv_usec;
   time_h_slice = time_h_end - time_h_start; 

   time_d_sum = time_d_sum + time_d[repcounter]; time_h_sum = time_h_sum + time_h[repcounter];
   printf("%f %d %f %d\n",time_d[repcounter],time_d_slice,time_h[repcounter],time_h_slice); 

   free(a_h);
   free(b_h);
   cudaFree(a_d);
   cudaFree(b_d);

 }
  
    time_dev_avg = time_d_sum/repcount; time_host_avg = time_h_sum/repcount;
    printf("%d %1f %1f\n",n,time_dev_avg,time_host_avg);

 }

   return(0);

}   
 

```

I do not need to run the program completely, I am running just to line 72 or:

printf("%f %d %f %d\n",time_d[repcounter],time_d_slice,time_h[repcounter],time_h_slice);
   
Now I run one step past the line to see the printf output or line 73. There is where the problem arises. 

Four number are printed out on a line and they should related.

The first two numbers should be the same and the last two numbers should be the same. 

As one can see from the code I am just calculating the time slice two different ways (for item d and item h), but since it applies to the same data the answers should be the same. 

They are not.

For example in my initial run tp line 72 (the line in question) and I get the following output.

43.000 1887546091 3.000 1887546051  

Now these numbers clearly not the same for the first two and the last two. It is not even close.

What is going on?

Newport_j

---

### Post by talonmies on 2010-02-12
The format for the second and lasts arguments of that print statement is wrong - the floating point values are being interpreted as integers. The compiler should issue a warning in such cases.

---

### Post by newport_j on 2010-02-12
The complier issued no warnings; but you are right. I changed it to %i from %f and the output still disagrees. You are correct about the printf statement, but why does the program still output nonsense on the second and fourth numbers printed out? As I said before: the first and second numbers should be the same and the third and fourth numbers should be the same. They are not, and that is what I posted the question about.

newport_j

---

### Post by talonmies on 2010-02-12
> **newport_j said:**
> The complier issued no warnings; but you are right. I changed it to %i from %f and the output still disagrees. 

Err no. Change them all to %f (%f for floating point). It is the pair of %d formats (%d is signed integer) in this:
```
printf("%f %d %f %d\n",time_d[repcounter],time_d_slice,time_h[repcounter],time_h_slice);
```that are wrong.

---

### Post by MadCow108 on 2010-02-12
from the code you posted their not the same
you multiply them with by factor 10 different numbers

---

### Post by newport_j on 2010-02-16
Okay, the following is my new code. I have changed ti to what I think are your recommendations.
 The change is only i the printf file

printf("%f %d %f %d\n",
time_d[repcounter],time_d_slice,time_h[repcounter],time_h_slice); 




```


#include <iostream>
#include <cuda.h>
#include "sys/time.h"

__global__ void vecMult_d(int *A, int *B, int N)
{    
    int i = blockIdx.x * blockDim.x + threadIdx.x;
    if(i<N) { B[i]=A[i]*2; } 
}

void vecMult_h(int *A, int*B, int N)
{
   for(int i=0;i<N;i++) { B[i] = A[i]*2; }
}

int main()  {
   int  *a_h, *b_h;   //pointers to host memory; aka CPU 
   int  *a_d, *b_d;   //pointers to device memory, aka GPU
   int block_size,grid_size,n=501,ncounter,ncount=100,repcounter,repcount=100,time_d_start,time_d_end,time_h_start,time_h_end,time_d_slice,time_h_slice;
   struct timeval t1_start,t1_end,t2_start,t2_end;
   double time_dev_avg, time_host_avg, time_d[repcount], time_h[repcount], time_d_sum, time_h_sum;

// Start a LOOP for many trials of matrix classes
   for (ncounter = 0; ncounter<ncount; ncounter++)
   {
   n = 501 + 500*ncounter, time_d_sum = 0; time_h_sum = 0;




for (repcounter = 0; repcounter<repcount; repcounter++)
{

// allocate arrays on host
   a_h = (int *)malloc(sizeof(int)*n);
   b_h = (int *)malloc(sizeof(int)*n);   

// allocate arrays on device
   cudaMalloc((void **)&a_d,n*sizeof(int));
   cudaMalloc((void **)&b_d,n*sizeof(int));
   block_size = 64;
   grid_size = (int) ((n-1)/block_size)+1;

   for(int j=0;j<n;j++) a_h[j]=j; 


// GPU
   cudaMemcpy(a_d, a_h, n*sizeof(int),cudaMemcpyHostToDevice);
   gettimeofday(&t1_start,0);
   vecMult_d<<<grid_size,block_size>>>(a_d,b_d,n);
   cudaThreadSynchronize();
   gettimeofday(&t1_end,0); 
   cudaMemcpy(b_h,b_d,n*sizeof(int),cudaMemcpyDeviceToHost);


// CPU
   gettimeofday(&t2_start,0);
   vecMult_h(a_h,b_h,n);
   gettimeofday(&t2_end,0);

   time_d[repcounter] = (t1_end.tv_sec-t1_start.tv_sec)*1000000 + t1_end.tv_usec - t1_start.tv_usec; 
   time_d_start = t1_start.tv_sec*100000 + t1_start.tv_usec;
   time_d_end   = t1_end.tv_sec*1000000 + t1_end.tv_usec;
   time_d_slice = time_d_end - time_d_start;

   time_h[repcounter] = (t2_end.tv_sec-t2_start.tv_sec)*1000000 + t2_end.tv_usec - t2_start.tv_usec; 
   time_h_start = t2_start.tv_sec*100000 + t2_start.tv_usec;
   time_h_end   = t2_end.tv_sec*1000000 + t2_end.tv_usec;
   time_h_slice = time_h_end - time_h_start; 

   time_d_sum = time_d_sum + time_d[repcounter]; time_h_sum = time_h_sum + time_h[repcounter];
   printf("%f %d %f %d\n",time_d[repcounter],time_d_slice,time_h[repcounter],time_h_slice); 

   free(a_h);
   free(b_h);
   cudaFree(a_d);
   cudaFree(b_d);

 }
  
    time_dev_avg = time_d_sum/repcount; time_host_avg = time_h_sum/repcount;
    printf("%d %1f %1f\n",n,time_dev_avg,time_host_avg);

 }

   return(0);

}   
 

```


It still does not give the right answers. In fact at times it gives a negative answer and that is for the time! I am not sure what is causing the error.

As you can see I am calculating the start time two different ways (first and second number) and they should be the same, I am calculating the end time two different ways (third and fourth number) and they should be the same. What is the problem here? I am not seeing how such a simple calculation can be so far wrong.

Any help appreciated.

Newport_j

---

### Post by talonmies on 2010-02-16
Someone else already pointed out the main mistake. You have inconsistent conversion factors in the microsecond calculations for time_d_start and time_h_start, you are multiplying by 10&#8309; not 10&#8310; which is giving a huge difference between the starting and ending times.

Initially I thought it was invalid float to integer conversion in the print statement, but I was wrong.

---

### Post by newport_j on 2010-02-16
Yes, that was it. Thank you very much.

Newport_j

---

