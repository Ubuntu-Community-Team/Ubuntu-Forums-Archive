---
title: "Code Error in C/CUDA Program"
date: 2009-12-11
forum: Programming Talk
---

### Post by newport_j on 2009-12-11
When I run the following program (taken from the CUDA programming manual) I get the compiler esponse shown below the code

```


#include <stdio.h>
#include <stdlib.h>
#include <cuda.h>
#include <cuda_runtime.h>
#include <time.h>

// Matrices will be stored in row major order
// M(row, col) = *(M.elements + row * M.width + col)
typedef struct  {
       int width;
       int height;
       int stride;
       float *elements;
} Matrix;

// Thread block size
#define BLOCK_SIZE 16

// Get a matrix element
__device__ float GetElement(const Matrix A, int row, int col)
{
    return A.elements[row * A.stride + col];
}
//Set a matrix element
__device__ void SetElement(Matrix A, int row, int col, float value)
{
  A.elements[row * A.stride + col] = value;
}

//Get the Block_SIZExBLOCK_SIZE sub-matrix Asub of A that is
//located col sub-mtraices to the right and row sub-matrix down 
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

    //Invoke kernel 
    dim3 dimBlock(BLOCK_SIZE, BLOCK_SIZE);
    dim3 dimGrid(B.width / dimBlock.x + 1, A.height / dimBlock.y + 1);
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
    //Block row and column
    int blockRow = blockIdx.y;
    int blockCol = blockIdx.x;
 
    // Each thread computes one sub-matrix Csub of C
    Matrix Csub = GetSubMatrix(C, blockRow, blockCol); 

    // Each thread computes one element of C
    // by accumulating results into Cvalue
    float Cvalue = 0;

    // Thread row and column within Csub
    int row = threadIdx.y;
    int col = threadIdx.x;

    // Loop over all the sub-matrices of A and B that are
    // required to compter Csub
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
    As[row][col] = GetElement[Asub, row, col];
    Bs[row][col] = GetElement[Asub, row, col];

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

  // Write to device meory
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

   int size = 10;
   int i, j;
   int print = true;
   Matrix A;
   Matrix B;
   Matrix C;
   Matrix D;
 

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



   printf("matrix generation\n");

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


     timedate();
     printf("GPU matrix multiplication\n");
     matrixMulGPU(A, B, C);
     timedate();

     timedate();
     printf("CPU matrix multiplication\n");
     matrixMulCPU(A, B, D);
     timedate();


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
            printf("%f  ",D.elements[i*size + j]);
         }
          printf("\n");

    }
  }

}








```example_eff.cu(126): warning: expression has no effect

example_eff.cu(126): error: expression must be a pointer to a complete object type

example_eff.cu(127): warning: expression has no effect

example_eff.cu(127): warning: expression has no effect

example_eff.cu(127): error: expression must be a pointer to a complete object type

2 errors detected in the compilation of "/tmp/tmpxft_00002848_00000000-7_example_eff.cpp1.ii".


Now lines 126 & 127 are now separately shown. 

// Load Asub and Bsub from device memory to shared memory
    // Each thread loads one element of each sub-matrix
    As[row][col] = GetElement[Asub, row, col];
    Bs[row][col] = GetElement[Asub, row, col];


I am unsure as to why the errors are appearing. It seems to be a c language error, not a CUDA error. It is also generating four warnings based on lines 126 & 127. What is wrong with these two lines of code?


Respectfully,

Newport_j

---

### Post by Trebaruna on 2009-12-11
In line 20 you define a function GetElement(), so it seems you need parentheses instead of square brackets.

Also, I think you're in the wrong forum ;)

EDIT: I know nothing of CUDA so it might be syntax I just do not know.

---

### Post by newport_j on 2009-12-11
Thank you. I will try it. I thought that this was the correct forum considering that it was a syntax error.

Thank you!

Respectfully,

Newport_j

---

### Post by Trebaruna on 2009-12-11
I believe this forum is for Ubuntu beginners, not beginning programmers as far as I know. Don't worry about it, though; if there's a problem a moderator will surely step in and save the day.

Good luck with CUDA!

---

### Post by newport_j on 2009-12-11
Show me explicitly where I am going wrong. I am not sure the way you get to line 20. I want to check it. But I think, that you and I count lines differently. It seems that I am unable to find the line (with confidence) that you say is wrong. Just desgnate a different way.


Newport_j

---

### Post by avidday on 2009-12-11
Try this:

```
    // Load Asub and Bsub from device memory to shared memory
    // Each thread loads one element of each sub-matrix
    As[row][col] = GetElement(Asub, row, col);
    Bs[row][col] = GetElement(Asub, row, col);

```

and maybe reading a book on C programming. I am not sure how you expect to write CUDA programs without at least an elementary grasp of the C language. This is at least the second time you have posted questions with code containing improper use of (),  [], and {}.

---

