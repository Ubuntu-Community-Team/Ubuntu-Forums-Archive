---
title: "Variable set but never used"
date: 2010-02-12
forum: Programming Talk
---

### Post by newport_j on 2010-02-12
The following c errors were received when I complied the code shown below.

 

cuda_two.cu(19): warning: variable "time_d_slice" was set but never used

cuda_two.cu(19): warning: variable "time_h_slice" was set but never used

cuda_two.cu(19): warning: variable "time_d_slice" was set but never used

cuda_two.cu(19): warning: variable "time_h_slice" was set but never used

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
   time_d_end   = t1_end.tv_sec*1000000 + t2_end.tv_usec;
   time_d_slice = time_d_end - time_d_start;

   time_h[repcounter] = (t2_end.tv_sec-t2_start.tv_sec)*1000000 + t2_end.tv_usec - t2_start.tv_usec; 
   time_h_start = t2_start.tv_sec*100000 + t2_start.tv_usec;
   time_h_end   = t2_end.tv_sec*1000000 + t2_end.tv_usec;
   time_h_slice = time_h_end - time_h_start; 

   time_d_sum = time_d_sum + time_d[repcounter]; time_h_sum = time_h_sum + time_h[repcounter];

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


I am not sure what it is telling me. I use both variables in  the lower part of the program. Specifically the lines:

time_d_slice = time_d_end - time_d_start;

time_h_slice = time_h_end - time_h_start; 


Now I am not sure what they mean. It seems that both variables are set and are used.


Newport_j

---

### Post by talonmies on 2010-02-12
> **newport_j said:**
> The following c errors were received when I complied the code shown below.

 

cuda_two.cu(19): warning: variable "time_d_slice" was set but never used

cuda_two.cu(19): warning: variable "time_h_slice" was set but never used

cuda_two.cu(19): warning: variable "time_d_slice" was set but never used

cuda_two.cu(19): warning: variable "time_h_slice" was set but never used

As the text says, those are not errors, they are warnings - hints from the compiler that your code compiles but might have unintended consequences.


> I am not sure what it is telling me. I use both variables in  the lower part of the program. Specifically the lines:

time_d_slice = time_d_end - time_d_start;

time_h_slice = time_h_end - time_h_start; 


That is setting the variables, but you don't use them after that. That is what gcc is telling you. If English isn't your native language and you can't understand the compiler diagnostics, you should be able to set your locale and get them in your native language.

Hope this helps.

---

### Post by newport_j on 2010-02-12
I have been debugging a much more complicated program. It also uses timers. I remember this one that I got from the internet. I just wanted to run the program in Nemiver past the statements where they variables were set and then place my cursor on them to see what their values were. Anything beyond that seemed superfluous. Why use them in a printf statement when it is so much easier to just place a cursor on them.

It did help.


Newport_j

---

### Post by talonmies on 2010-02-12
If the warnings bother you, they can be turned off with command line arguments. You can also do something dirty like

```

(void)time_d_slice;
(void)time_h_slice;

```in the code after you set them and the warnings will go away. But do look at getting your language settings right, and gcc will give you easier to understand warnings in your native tongue. The English ones can be rough to understand for non-English speakers. I often have to switch back from English to work out what some of them are.

---

### Post by CptPicard on 2010-02-12
I find anything else than non-English compiler outputs to be utterly non-decipherable, as I have to then work out the translation. Google works much better on English if one needs help :p

---

