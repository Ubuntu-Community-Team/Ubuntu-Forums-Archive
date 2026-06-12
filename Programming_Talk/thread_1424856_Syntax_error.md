---
title: "Syntax error?"
date: 2010-03-08
forum: Programming Talk
---

### Post by newport_j on 2010-03-08
I am trying to get different times for matrix multiplication using different processors (CPU and GPU).

I want to put the times in a file with the first column the matrix size (it is a square matrix). The second column is the time for one processor; and the third is the time for the third processor.

I find it easier to set the times to separate variables. 

However, the code below is not working. 

GPU_time = cutGetTimerValue(timer);

It gives a segmentation fault, likewise for CPU. I cannot see why. What is wrong here?

Newport_j


```

// create and start timer
     unsigned int timer = 0;
     cutilCheckError(cutCreateTimer(&timer));
     cutilCheckError(cutStartTimer(timer));
     printf("\n");   
     printf("GPU matrix multiplication\n");
     matrixMulGPU(A, B, C);
// stop and destroy timer
     cutilCheckError(cutStopTimer(timer));
     printf("GPU Processing time: %f (ms) \n", cutGetTimerValue(timer));
     cutilCheckError(cutDeleteTimer(timer));
     GPU_time = cutGetTimerValue(timer);
     printf("\n");
     printf("\n");    


// create and start timer
     cutilCheckError(cutCreateTimer(&timer));
     cutilCheckError(cutStartTimer(timer));
     printf("\n");
     printf("CPU matrix multiplication\n");
     matrixMulCPU(A, B, D);
//stop and destroy timer
     cutilCheckError(cutStopTimer(timer));
     printf("CPU Processing time: %f (ms) \n", cutGetTimerValue(timer));
     CPU_time = cutGetTimerValue(timer); 
     cutilCheckError(cutDeleteTimer(timer));
     printf("\n");
     printf("\n");

     printf("%d %1f %1f\n",size,CPU_time,GPU_time);  

```

---

### Post by talonmies on 2010-03-08
Given this looks to be something to do with nvidia CUDA libraries, if my Google-fu is good, maybe a GPGPU support forum might be a better place to ask this. No-one here is going to be able to help you, especially with the paucity of information you have provided. 

I have found the secret to getting useful help is firstly knowing what question to ask, and secondly knowing what venue is the best place to ask it. I suspect this question fails on both accounts.

---

### Post by newport_j on 2010-03-08
Okay, let's try this:

```

#include <stdio.h>
#include <stdlib.h>
#include <cuda.h>
#include <cuda_runtime.h>
#include <time.h>

//includes project
#include <cutil_inline.h>


// Matrices will be stored in row major order
// M(row, col) = *(M.elements + row * M.stride + col)
typedef struct  {
       int width;
       int height;
       int stride;
       float *elements;
} Matrix;

// Thread block size
#define BLOCK_SIZE 10

// Get a matrix element
__device__ float GetElement(const Matrix A, int row, int col)
{
    return A.elements[row * A.stride + col];
}
// Set a matrix element
__device__ void SetElement(Matrix A, int row, int col, float value)
{

  A.elements[row * A.stride + col] = value;
}

// Get the BLOCK_SIZExBLOCK_SIZE sub-matrix Asub of A that is
// located col sub-matrices to the right and row sub-matrix down 
// from the upper-left corner of A
__device__ Matrix GetSubMatrix(Matrix A, int row, int col)

{
   Matrix Asub;
   Asub.width    = BLOCK_SIZE;
   Asub.height   = BLOCK_SIZE;
   Asub.stride   = A.stride;
   Asub.elements = &A.elements[A.stride * BLOCK_SIZE * row + BLOCK_SIZE * col];

   return Asub;
}


// Forward declaration of the matrix multiplication kernel
__global__ void MatMulKernel(const Matrix, const Matrix, Matrix);


// Matrix Multiplication - Host code
// Matrix dimensions are assumed to be multiples of BLOCK_SIZE
void matrixMulGPU(const Matrix A, const Matrix B, const Matrix C)
{
    // Load A and B to device memory
    Matrix d_A;
    d_A.width = d_A.stride = A.width; d_A.height = A.height;    
    size_t size = A.width * A.height * sizeof(float);
    cudaMalloc((void**)&d_A.elements, size);
    cudaMemcpy(d_A.elements, A.elements, size, cudaMemcpyHostToDevice);

    Matrix d_B;
    d_B.width = d_B.stride = B.width; d_B.height = B.height;    
    size = B.width * B.height * sizeof(float);
    cudaMalloc((void**)&d_B.elements, size);
    cudaMemcpy(d_B.elements, B.elements, size, cudaMemcpyHostToDevice);

    // Allocate C in device memory
    Matrix d_C;
    d_C.width = d_C.stride = C.width; d_C.height = C.height;    
    size = C.width * C.height * sizeof(float);
    cudaMalloc((void**)&d_C.elements, size);

    // Invoke kernel 
    dim3 dimBlock(BLOCK_SIZE, BLOCK_SIZE);
    dim3 dimGrid(B.width / dimBlock.x, A.height / dimBlock.y + 1);
    MatMulKernel<<<dimGrid, dimBlock>>>(d_A, d_B, d_C); 


    // Read C from device memory
    cudaMemcpy(C.elements, d_C.elements, size, cudaMemcpyDeviceToHost);
   
    // Free device memory
    cudaFree(d_A.elements);
    cudaFree(d_B.elements);
    cudaFree(d_C.elements);

}

// Matrix multiplication kernel called by MatMul()
__global__ void MatMulKernel(Matrix A, Matrix B, Matrix C)
{
    // Block row and column
    int blockRow = blockIdx.y;
    int blockCol = blockIdx.x;
 
    // Each thread block computes one sub-matrix Csub of C
    Matrix Csub = GetSubMatrix(C, blockRow, blockCol); 

    // Each thread computes one element of C
    // by accumulating results into Cvalue
    float Cvalue = 0;

    // Thread row and column within Csub
    int row = threadIdx.y;
    int col = threadIdx.x;

    // Loop over all the sub-matrices of A and B that are
    // required to compute Csub
    // Multiply each pair of sub-matrices together
    // and accumulate the results
    for (int m = 0; m < (A.width / BLOCK_SIZE); ++m) {

    // Get sub-matrix Asub of A
    Matrix Asub = GetSubMatrix(A, blockRow, m);

    // Get sub-matrix of B
    Matrix Bsub = GetSubMatrix(B, m, blockCol);
 
    // Shared memory used to store Asub and Bsub respectivley
    __shared__  float As[BLOCK_SIZE][BLOCK_SIZE];
    __shared__  float Bs[BLOCK_SIZE][BLOCK_SIZE];

   
    // Load Asub and Bsub from device memory to shared memory
    // Each thread loads one element of each sub-matrix
    As[row][col] = GetElement(Asub, row, col);
    Bs[row][col] = GetElement(Bsub, row, col);

    // Synchronize to make sure the sub-matrices are loaded
    // before starting the computation
    __syncthreads();

    // Multiply Asub and Bsub together
    for (int e = 0; e < BLOCK_SIZE; ++e)
        Cvalue += As[row][e] * Bs[e][col];

    // Synchronize to make sure that the proceeding
    // computation is done before loading the two new
    // sub-matrics of A and B in the next iteration
    __syncthreads();
  }

  // Write to device memory
  // Each thread writes one element
  SetElement(Csub, row, col, Cvalue);
}   
 
           

float floatRand(float MaxVal) {
    return ( (float)rand()  / (float)RAND_MAX ) * MaxVal;
}

void timedate() {
    time_t temps_act;
    time(&temps_act);
    printf("%s\n", ctime(&temps_act));
}

void matrixMulCPU(Matrix M, Matrix N, Matrix P) {

    int i, j, k;

    for(i=0; i<M.height; i++) {
        for(j=0; j<N.width; j++) { 
            for(k=0; k<M.width; k++) {
                P.elements[i*N.width + j] += M.elements[i*M.width + k]
                                           * N.elements[k*N.width + j];
            }
        }
    }
}

int main()  {

   int size;
   int i, j;
   int print = true;
   Matrix A;
   Matrix B;
   Matrix C;
   Matrix D;
   double GPU_time,CPU_time;
   FILE *fid;
 
   for(int k=0; k<11; k++)  { 
   size = 10*(k+1);
   if(k>0)print = false;

   A.width = size;
   A.height = size;
   A.elements = (float*) malloc(A.width*A.height*sizeof(float));

   B.width = size;
   B.height = size;
   B.elements = (float*) malloc(B.width*B.height*sizeof(float));

   C.width = size;
   C.height = size;
   C.elements = (float*) malloc(C.width*C.height*sizeof(float));

   D.width = size;
   D.height = size;
   D.elements = (float*) malloc(D.width*D.height*sizeof(float));

   printf("\n");
   printf("\n");
   printf("matrix generation\n");
   printf("matrix size %i ",size);

   srand ( time(NULL)  );

   for(i=0; i<size*size; i++)  {
       A.elements[i] = 2; //floatRand(2);
       B.elements[i] = 2; //floatRand(2);
//       A.elements[i] = 3;
//       B.elements[i] = 3;
       C.elements[i] = 0;
       D.elements[i] = 0;

    }

  if(print) {
      printf("A =\n");
      for(i=0; i<A.height; i++) {
          for(j=0; j<A.width; j++) {
            printf("%f ",A.elements[i*size + j]);
          }
         printf("\n");
      }
      printf("\n\n");
      printf("B =\n");
      for(i=0; i<B.height; i++) {
          for(j=0; j<B.width; j++) {
            printf("%f ",B.elements[i*size + j]);
          }
         printf("\n");
      }

    }   

fid = fopen("Matrix_eff.out","w");
// create and start timer
     unsigned int timer = 0;
     cutilCheckError(cutCreateTimer(&timer));
     cutilCheckError(cutStartTimer(timer));
     printf("\n");   
     printf("GPU matrix multiplication\n");
     matrixMulGPU(A, B, C);
// stop and destroy timer
     cutilCheckError(cutStopTimer(timer));
     printf("GPU Processing time: %f (ms) \n", cutGetTimerValue(timer));
     GPU_time = cutGetTimerValue(timer);
     cutilCheckError(cutDeleteTimer(timer));
     printf("\n");
     printf("\n");    


// create and start timer
     cutilCheckError(cutCreateTimer(&timer));
     cutilCheckError(cutStartTimer(timer));
     printf("\n");
     printf("CPU matrix multiplication\n");
     matrixMulCPU(A, B, D);
//stop and destroy timer
     cutilCheckError(cutStopTimer(timer));
     printf("CPU Processing time: %f (ms) \n", cutGetTimerValue(timer));
     CPU_time = cutGetTimerValue(timer);  
     cutilCheckError(cutDeleteTimer(timer));
     printf("\n");
     printf("\n");
     printf(fid,"%d %1f %1f\n",size,GPU_time,CPU_time); 
     fclose(fid);   

     //print result
     if(print) {
         printf("C =\n");
         for(i=0; i<C.height; i++)  {
         for(j=0; j<C.width; j++)  {
             printf("%f ",C.elements[i*size + j]);
          }   
          printf("\n"); 
       } 
       
        printf("\n\n");
        printf("D =\n");
        for(i=0; i<D.height; i++) {
        for(j=0; j<D.width; j++) {
            printf("%f ",D.elements[i*size + j]);
         }
          printf("\n");
    }
  }
 }
}




         


 
 
 
     
     


   





```

compilation of this code results in the following error: 

argument of type "FILE *" is incompatible with parameter of type "const char *".

I am unsure how to correct it.


newport_j

---

### Post by dwhitney67 on 2010-03-08
Use fprintf(), not printf() in the statement below:
```

printf(fid,"%d %1f %1f\n",size,GPU_time,CPU_time);

```

---

