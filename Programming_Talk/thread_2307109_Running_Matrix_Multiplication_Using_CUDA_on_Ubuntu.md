---
title: "Running Matrix Multiplication Using CUDA on Ubuntu 14.04"
date: 2015-12-22
forum: Programming Talk
---

### Post by pradyot on 2015-12-22
Hi,

  I am playing around with the Matrix Multiplication on CUDA. I am trying to find out the max amount of dimension of the matrix i can multiply.
Here is my device query:

```
server@HP-Z230-Tower-Ws2:/usr/local/cuda/samples/1_Utilities/deviceQuery$ ./deviceQuery 
./deviceQuery Starting...

 CUDA Device Query (Runtime API) version (CUDART static linking)

Detected 1 CUDA Capable device(s)

Device 0: "Quadro 410"
  CUDA Driver Version / Runtime Version          7.5 / 7.0
  CUDA Capability Major/Minor version number:    3.0
  Total amount of global memory:                 503 MBytes (527826944 bytes)
  ( 1) Multiprocessors, (192) CUDA Cores/MP:     192 CUDA Cores
  GPU Max Clock rate:                            706 MHz (0.71 GHz)
  Memory Clock rate:                             891 Mhz
  Memory Bus Width:                              64-bit
  L2 Cache Size:                                 131072 bytes
  Maximum Texture Dimension Size (x,y,z)         1D=(65536), 2D=(65536, 65536), 3D=(4096, 4096, 4096)
  Maximum Layered 1D Texture Size, (num) layers  1D=(16384), 2048 layers
  Maximum Layered 2D Texture Size, (num) layers  2D=(16384, 16384), 2048 layers
  Total amount of constant memory:               65536 bytes
  Total amount of shared memory per block:       49152 bytes
  Total number of registers available per block: 65536
  Warp size:                                     32
  Maximum number of threads per multiprocessor:  2048
  Maximum number of threads per block:           1024
  Max dimension size of a thread block (x,y,z): (1024, 1024, 64)
  Max dimension size of a grid size    (x,y,z): (2147483647, 65535, 65535)
  Maximum memory pitch:                          2147483647 bytes
  Texture alignment:                             512 bytes
  Concurrent copy and kernel execution:          Yes with 1 copy engine(s)
  Run time limit on kernels:                     No
  Integrated GPU sharing Host Memory:            No
  Support host page-locked memory mapping:       Yes
  Alignment requirement for Surfaces:            Yes
  Device has ECC support:                        Disabled
  Device supports Unified Addressing (UVA):      Yes
  Device PCI Domain ID / Bus ID / location ID:   0 / 1 / 0
  Compute Mode:
     < Default (multiple host threads can use ::cudaSetDevice() with device simultaneously) >

deviceQuery, CUDA Driver = CUDART, CUDA Driver Version = 7.5, CUDA Runtime Version = 7.0, NumDevs = 1, Device0 = Quadro 410
Result = PASS


```

I am using Intel i5 4590 as processor 

Here is my MATRIX MULTIPLICATION CODE

```

// FILE NAME: matmul.cu
#include<cuda.h>
#include<stdio.h>
#include<stdlib.h> 
#include <math.h>





//Matrix multiplication kernel - thread specification
__global__ void MatrixMulKernel(int *Md, int *Nd, int *Pd, int Width) {
    //2D Thread ID
    int col = blockIdx.x*blockDim.x+threadIdx.x;
    int row = blockIdx.y*blockDim.y+threadIdx.y;

    //Pvalue stores the Pd element that is computed by the thread
    int Pvalue = 0;
    if(col<Width && row < Width)
    {
            for(int k = 0; k < Width ; ++k) 
            {
                int Mdelement = Md[row*Width + k];
                int Ndelement = Nd[k*Width + col];
                Pvalue += (Mdelement*Ndelement);
        
            }
            Pd[row*Width + col] = Pvalue;
    }
}





int main(void) {
    
  unsigned  int Width ;
    printf("\n\n Enter Width:");
    scanf("%d",&Width);

        int M[Width*Width], N[Width*Width], P[Width*Width];
    int *Md, *Nd, *Pd;

    for(int i = 0; i < (Width*Width) ; i++) {
        M[i] = 5;
        N[i] = 5;
        P[i] = 0;
    }





    unsigned long int size = Width*Width*sizeof(int);
  

    //Transfer M and N to device memory
    cudaMalloc((void**)&Md, size);
    cudaMemcpy(Md,M,size,cudaMemcpyHostToDevice);

    cudaMalloc((void**)&Nd, size);
    cudaMemcpy(Nd,N,size,cudaMemcpyHostToDevice);

    //Allocate P on the device
    cudaMalloc((void**)&Pd,size);

    //Setup the execution configuration
    dim3 dimBlock(Width,Width);
    dim3 dimGrid(1,1);





    if (Width*Width > 1024)
    {
        printf("\n\n enter inside if condi\n\n");
        dimGrid.x = (Width-1)/32+1;
            dimGrid.y = (Width-1)/32+1;
    
        dimBlock.x = 32;
            dimBlock.y =32;



    }




    printf(" Width=%d  dimBlock.x = %d   dimBlock.y = %d   dimGrid.x = %d    dimGrid.y = %d \n\n\n\n",Width, dimBlock.x, dimBlock.y ,   dimGrid.x ,    dimGrid.y);
  

     
    //Launch the device computation threads!
    MatrixMulKernel<<<dimGrid,dimBlock>>>(Md,Nd,Pd,Width);

    //Transfer P from device to host
    cudaMemcpy(P,Pd,size,cudaMemcpyDeviceToHost);

    //Free device matrices
    cudaFree(Md);
    cudaFree(Nd);
    cudaFree(Pd);





    int *cpu_C;
    cpu_C=new int[Width*Width];

    // Now do the matrix multiplication on the CPU
    int sum;
    for (int row=0; row<Width; row++){
        for (int col=0; col<Width; col++){
            sum = 0.f;
            for (int n=0; n<Width; n++){
                sum += M[row*Width+n]*N[n*Width+col];
            }
            cpu_C[row*Width+col] = sum;
        }
    }


//Output result matrix
/*
     for (int row=0; row<Width*Width; row++){
            
      
            printf("%d   ",P[row]) ;                                                                                                                                                                              
            if((row+1)%Width==0)
            printf("\n");
        }

*/




    int err = 0;
    // Check the result and make sure it is correct

     for (int row=0; row<Width; row++){
        for (int col=0; col<Width; col++){
      
            err += cpu_C[row * Width + col] - P[row * Width + col];                                                                                                                                                                                        
        }
    }

                                                                                                                                                                                                                                                                     
    if(err!=0)
            printf( "\n\nError in matmul\n\n\n");
    else 
        printf("\n\nNo ERROR\n\n\n");

    return 0;


}




```

Compiled with 
```

$nvcc matmul.cu
$./a.out

```
Here it gets tricky. The max width of the matrix without 

```

Segmentation fault (core dumped)



```

is Width=832

I browsed around the error and found the solution in 


[http://www.cs.nyu.edu/exact/core/doc/stackOverflow.txt](http://www.cs.nyu.edu/exact/core/doc/stackOverflow.txt)

so I resized my ulimit by

```

$ ulimit -s 32768

```

now the max Wdth size i can take without 

```

Segmentation fault (core dumped)



```

is Width = 1672.

My question is why does the parallel program depending on the the stack memory of the CPU rather than of GPU and What changes must I implement to run a 10000 x 10000 matrix with the above code.

---

### Post by QIII on 2015-12-22
*Moved to **Programming Talk***

---

### Post by spjackson on 2015-12-22
I don't think your problem is anything to do with CUDA. Simply
> 
```

        int M[Width*Width], N[Width*Width], P[Width*Width];


```

is a core dump waiting to happen for large values of Width. You probably want to malloc these.
```

       int * M = (int *) malloc(Width*Width*sizeof(int));

```
etc.

---

### Post by pradyot on 2015-12-22
Thank you [**[COLOR=#000000]spjackson[/COLOR]**]("http://ubuntuforums.org/member.php?u=1128302")
This which seems like such a small error had me troubled for 2 days. With corrections which you pointed out i was able to run the program with high number of dimension. 
For anyone looking for a simple Matrix multiplication in CUDA here is the completed code tested till 4000 x 4000 

```

#include<cuda.h>
#include<stdio.h>
#include<stdlib.h> 
#include <math.h>





//Matrix multiplication kernel - thread specification
__global__ void MatrixMulKernel(int *Md, int *Nd, int *Pd, int Width) {
    //2D Thread ID
    int col = blockIdx.x*blockDim.x+threadIdx.x;
    int row = blockIdx.y*blockDim.y+threadIdx.y;

    //Pvalue stores the Pd element that is computed by the thread
    int Pvalue = 0;
    if(col<Width && row < Width)
    {
            for(int k = 0; k < Width ; ++k) 
            {
                int Mdelement = Md[row*Width + k];
                int Ndelement = Nd[k*Width + col];
                Pvalue += (Mdelement*Ndelement);
        
            }
            Pd[row*Width + col] = Pvalue;
    }
}





int main(void) {
    
  unsigned  int Width ;
    printf("\n\n Enter Width:");
    scanf("%d",&Width);

//        int M[Width*Width], N[Width*Width], P[Width*Width];

  int * M = (int *) malloc(Width*Width*sizeof(int));
  int * N = (int *) malloc(Width*Width*sizeof(int));
  int * P = (int *) malloc(Width*Width*sizeof(int));
    int *Md, *Nd, *Pd;

    for(int i = 0; i < (Width*Width) ; i++) {
        M[i] = 5;
        N[i] = 5;
        P[i] = 0;
    }





    unsigned long int size = Width*Width*sizeof(int);
  

    //Transfer M and N to device memory
    cudaMalloc((void**)&Md, size);
    cudaMemcpy(Md,M,size,cudaMemcpyHostToDevice);

    cudaMalloc((void**)&Nd, size);
    cudaMemcpy(Nd,N,size,cudaMemcpyHostToDevice);

    //Allocate P on the device
    cudaMalloc((void**)&Pd,size);

    //Setup the execution configuration
    dim3 dimBlock(Width,Width);
    dim3 dimGrid(1,1);





    if (Width*Width > 1024)
    {
        printf("\n\n enter inside if condi\n\n");
        dimGrid.x = (Width-1)/32+1;
            dimGrid.y = (Width-1)/32+1;
    
        dimBlock.x = 32;
            dimBlock.y =32;



    }




    printf(" Width=%d  dimBlock.x = %d   dimBlock.y = %d   dimGrid.x = %d    dimGrid.y = %d \n\n\n\n",Width, dimBlock.x, dimBlock.y ,   dimGrid.x ,    dimGrid.y);
  

     
    //Launch the device computation threads!
    MatrixMulKernel<<<dimGrid,dimBlock>>>(Md,Nd,Pd,Width);

    //Transfer P from device to host
    cudaMemcpy(P,Pd,size,cudaMemcpyDeviceToHost);

    //Free device matrices
    cudaFree(Md);
    cudaFree(Nd);
    cudaFree(Pd);





    int *cpu_C;
    cpu_C=new int[Width*Width];

    // Now do the matrix multiplication on the CPU
    int sum;
    for (int row=0; row<Width; row++){
        for (int col=0; col<Width; col++){
            sum = 0.f;
            for (int n=0; n<Width; n++){
                sum += M[row*Width+n]*N[n*Width+col];
            }
            cpu_C[row*Width+col] = sum;
        }
    }


//Output result matrix
/*
     for (int row=0; row<Width*Width; row++){
            
      
            printf("%d   ",P[row]) ;                                                                                                                                                                              
            if((row+1)%Width==0)
            printf("\n");
        }

*/




    int err = 0;
    // Check the result and make sure it is correct

     for (int row=0; row<Width; row++){
        for (int col=0; col<Width; col++){
      
            err += cpu_C[row * Width + col] - P[row * Width + col];                                                                                                                                                                                        
        }
    }

                                                                                                                                                                                                                                                                     
    if(err!=0)
            printf( "\n\nError in matmul\n\n\n");
    else 
        printf("\n\nNo ERROR\n\n\n");

free(M);
free(N);
free(P);

    return 0;


}



```


Thank you for your valuable time :)

---

