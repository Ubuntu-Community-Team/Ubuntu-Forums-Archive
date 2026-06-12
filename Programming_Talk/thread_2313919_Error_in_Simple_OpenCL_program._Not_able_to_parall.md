---
title: "Error in Simple OpenCL program. Not able to parallelize"
date: 2016-02-16
forum: Programming Talk
---

### Post by pradyot on 2016-02-16
Hi,
    I am on the road to learn OpenCL.The following is my code for a simple Vector addition. 


File Name : main.c
```

#include <stdio.h>
#include <stdlib.h>
#include <CL/cl.h>

 
#define MAX_SOURCE_SIZE 9999999
 
int main(void) {
          int i;


    // size of each matrix as 1024

        const int LIST_SIZE = 1024;


//dynamic allocation of the matrices
        int *A = (int*)malloc(sizeof(int)*LIST_SIZE);
        int *B = (int*)malloc(sizeof(int)*LIST_SIZE);

//initialization
        for(i = 0; i < LIST_SIZE; i++) {
            A[i] = i;
            B[i] = LIST_SIZE - i;
        }



 
    // Load the kernel source code into the array source_str
        FILE *fp;
        char *source_str;
        size_t source_size;
 
        fp = fopen("vector_add_kernel.cl", "r");
        if (!fp) {
            fprintf(stderr, "Failed to load kernel.\n");
            exit(1);
        }
        source_str = (char*)malloc(MAX_SOURCE_SIZE);
source_str[MAX_SOURCE_SIZE+1]='\0';
        source_size = fread( source_str, 1, MAX_SOURCE_SIZE, fp);
        fclose( fp );

    // here the source_str contain the kernel code of this pgm
        // Use this to check the output of each API call

    cl_int ret;
    int j;

    // Discover and initialize the platforms

        cl_platform_id *platform_id;
    char* info;
        size_t infoSize;
        cl_uint ret_num_platforms;

//To print the selected platform



 ret = clGetPlatformIDs(5, NULL, &ret_num_platforms);

printf("\n the total no. of platforms detected is :%d\n",ret_num_platforms);


platform_id = (cl_platform_id *)malloc(sizeof(cl_platform_id) * ret_num_platforms);

 ret = clGetPlatformIDs(ret_num_platforms, platform_id, NULL);

         // get platform attribute value size
                clGetPlatformInfo(platform_id[1], CL_PLATFORM_NAME, 0, NULL, &infoSize);
                info = (char*) malloc(infoSize);
 
                // get platform attribute value
                    clGetPlatformInfo(platform_id[1], CL_PLATFORM_NAME, infoSize, info, NULL);

                    

                    printf("\n  Name of the platform selected: %s ", info);



    //Discover and initialize the devices
    


    cl_device_id device_id=NULL;   
    cl_uint ret_num_devices=1;
    ret = clGetDeviceIDs( platform_id[1], CL_DEVICE_TYPE_GPU, 1,&device_id, NULL);


// Print the selected device
    char* value;
        size_t valueSize;
    clGetDeviceInfo(device_id, CL_DEVICE_NAME, 0, NULL, &valueSize);
            value = (char*) malloc(valueSize);
            clGetDeviceInfo(device_id, CL_DEVICE_NAME, valueSize, value, NULL);
            printf("\nDevice selected name is: %s \n",value);
            free(value);



    // Create an OpenCL context
// Create a context using clCreateContext() and associate it with the devices



    cl_context context = clCreateContext( NULL, 1, &device_id, NULL, NULL, &ret);


    if (ret != CL_SUCCESS)
    {
        printf( "\n\n Could not create GPU context");
    
    }
    else
    {
        printf("\n\nno error in creatng context");
    }
    

    
    // Create a command queue
    cl_command_queue command_queue = clCreateCommandQueue(context, device_id, 0, &ret);

    // Create a command queue using clCreateCommandQueue(),
    // and associate it with the device you want to execute 
    // on
 
if (command_queue == NULL)
{
printf("\n\nFailed to create commandQueue for device 0");
exit(0);
}
    else
    {
        printf("\n\n no error in creating commandQueue");
    }













    // Create memory buffers on the device for each vector 

    // Use clCreateBuffer() to create a buffer object (d_A) 
    // that will contain the data from the host array A

    cl_mem a_mem_obj = clCreateBuffer(
                context, 
                CL_MEM_READ_ONLY, 
                LIST_SIZE * sizeof(int), 
                A, 
                &ret);

    // Use clCreateBuffer() to create a buffer object (d_B)
    // that will contain the data from the host array B
    cl_mem b_mem_obj = clCreateBuffer(
                context, 
                CL_MEM_READ_ONLY,
                        LIST_SIZE * sizeof(int), 
                B, 
                &ret);




    // Use clCreateBuffer() to create a buffer object (d_C) 
    // with enough space to hold the output data

    cl_mem c_mem_obj = clCreateBuffer(
                context, 
                CL_MEM_WRITE_ONLY, 
                       LIST_SIZE * sizeof(int), 
                NULL,
                &ret);
 
 
    // Create a program using clCreateProgramWithSource()


    // Create a program from the kernel source

        cl_program program = clCreateProgramWithSource(context, 1, (const char **)&source_str, (const size_t *)&source_size, &ret);

    if (program == NULL)
    {
        printf("Failed to create CL program from source.");
    
    }
    else
    {
        printf("\n\n no error in creating CL program from source");
    }



       // Build (compile) the program for the devices with clBuildProgram()
        // Build the program
    

    
ret = clBuildProgram(program, 1, &device_id, 0, 0, 0);
printf("\n\nbuild pgm returns code:%d\n\n",ret);




    if (ret != CL_SUCCESS)
    {
        // Determine the reason for the error
    
    


        size_t log_size;
        
        clGetProgramBuildInfo(program, device_id, CL_PROGRAM_BUILD_LOG, 0, NULL, &log_size);

        //char *buildLog=(*char)malloc(sizeof);

char *buildLog = calloc(log_size, sizeof(char));
        clGetProgramBuildInfo(program, device_id, CL_PROGRAM_BUILD_LOG,log_size, buildLog, NULL);
buildLog[log_size]='\0';
        printf("\nError in kernel BUILD PGM: %s\n ",buildLog);



    }
    

        // Create the OpenCL kernel

        cl_kernel kernel = clCreateKernel(program, "vector_add", &ret);
 

 if (ret != CL_SUCCESS)
    {
        printf("\nError at: clCreateKernel(get kernel function failed)\n");
        
    }


    // Associate the input and output buffers with the 
        // kernel  using clSetKernelArg()

        // Set the arguments of the kernel
        ret = clSetKernelArg(
            kernel, 
            0, 
            sizeof(cl_mem), 
            (void *)&a_mem_obj);

        ret = clSetKernelArg(
            kernel, 
            1, 
            sizeof(cl_mem), 
            (void *)&b_mem_obj);
  
      ret = clSetKernelArg(
            kernel, 
            2, 
            sizeof(cl_mem), 
            (void *)&c_mem_obj);
    ret = clSetKernelArg(
            kernel, 
            3, 
            sizeof(unsigned int), 
            &LIST_SIZE);
 
        // Define an index space (global work size) of work 
        // items for execution. A workgroup size (local work size) is not 
        // required, but can be used.
        // Execute the OpenCL kernel on the list

        size_t global_item_size = LIST_SIZE; // Process the entire lists
        size_t local_item_size = 64; // Divide work items into groups of 64



      // Execute the kernel by using 
        // clEnqueueNDRangeKernel().
        // 'globalWorkSize' is the 1D dimension of the 
        // work-items

    ret = clEnqueueNDRangeKernel(command_queue, kernel, 1, NULL, &global_item_size, &local_item_size, 0, NULL, NULL);
 
       if(ret== CL_SUCCESS) {
            printf("\n\nNO Error in clEnqueueNDRangeKernel\n");
        } 

    else {
            printf("\n Error clEnqueueNDRangeKernel\n");
        }


     // Use clEnqueueReadBuffer() to read the OpenCL output  
        // buffer (bufferC) 
        // to the host output array (C)
        // Read the memory buffer C on the device to the local variable C
        
    int *C = (int*)malloc(sizeof(int)*LIST_SIZE);
        ret = clEnqueueReadBuffer(
            command_queue, 
            c_mem_obj, 
            CL_TRUE, 
            0, 
                    LIST_SIZE * sizeof(int), 
            C, 
            0, 
            NULL, 
            NULL);
 
    // Display the result to the screen
int result= 1;
    for( i = 0; i < LIST_SIZE; i++) {
        if(C[i] != A[i]+B[i]) {
            result = 0;
            break;
        }
    }
    if(result==1) {
        printf("\nOutput is Correct\n");
    } else {
        printf("\nOutput is Incorrect\n");
    }

   // Free OpenCL resources
    // Clean up
    ret = clFlush(command_queue);
    ret = clFinish(command_queue);
    ret = clReleaseKernel(kernel);
    ret = clReleaseProgram(program);
    ret = clReleaseMemObject(a_mem_obj);
    ret = clReleaseMemObject(b_mem_obj);
    ret = clReleaseMemObject(c_mem_obj);
    ret = clReleaseCommandQueue(command_queue);
    ret = clReleaseContext(context);
    free(A);
    free(B);
    free(C);
    return 0;
}


```



The kernel  code for the above is :
Kernel File name: vector_add_kernel.cl


```

__kernel void vector_add(__global const int *A, __global const int *B, __global int *C, int N) {
 
    // Get the index of the current element to be processed
    int i = get_global_id(0);
 if(i<N)
{
    C[i] = A[i] + B[i];
}
    // Do the operation
    
}

```


The clinfo of my system is as follows:
```

Number of platforms:                 2
  Platform Profile:                 FULL_PROFILE
  Platform Version:                 OpenCL 1.2 AMD-APP (1445.5)
  Platform Name:                 AMD Accelerated Parallel Processing
  Platform Vendor:                 Advanced Micro Devices, Inc.
  Platform Extensions:                 cl_khr_icd cl_amd_event_callback cl_amd_offline_devices cl_amd_hsa 
  Platform Profile:                 FULL_PROFILE
  Platform Version:                 OpenCL 1.2 CUDA 7.5.23
  Platform Name:                 NVIDIA CUDA
  Platform Vendor:                 NVIDIA Corporation
  Platform Extensions:                 cl_khr_byte_addressable_store cl_khr_icd cl_khr_gl_sharing cl_nv_compiler_options cl_nv_device_attribute_query cl_nv_pragma_unroll cl_nv_copy_opts 


  Platform Name:                 AMD Accelerated Parallel Processing
Number of devices:                 1
  Device Type:                     CL_DEVICE_TYPE_CPU
  Vendor ID:                     1002h
  Board name:                     
  Max compute units:                 4
  Max work items dimensions:             3
    Max work items[0]:                 1024
    Max work items[1]:                 1024
    Max work items[2]:                 1024
  Max work group size:                 1024
  Preferred vector width char:             16
  Preferred vector width short:             8
  Preferred vector width int:             4
  Preferred vector width long:             2
  Preferred vector width float:             8
  Preferred vector width double:         4
  Native vector width char:             16
  Native vector width short:             8
  Native vector width int:             4
  Native vector width long:             2
  Native vector width float:             8
  Native vector width double:             4
  Max clock frequency:                 3393Mhz
  Address bits:                     64
  Max memory allocation:             2147483648
  Image support:                 Yes
  Max number of images read arguments:         128
  Max number of images write arguments:         8
  Max image 2D width:                 8192
  Max image 2D height:                 8192
  Max image 3D width:                 2048
  Max image 3D height:                 2048
  Max image 3D depth:                 2048
  Max samplers within kernel:             16
  Max size of kernel argument:             4096
  Alignment (bits) of base address:         1024
  Minimum alignment (bytes) for any datatype:     128
  Single precision floating point capability
    Denorms:                     Yes
    Quiet NaNs:                     Yes
    Round to nearest even:             Yes
    Round to zero:                 Yes
    Round to +ve and infinity:             Yes
    IEEE754-2008 fused multiply-add:         Yes
  Cache type:                     Read/Write
  Cache line size:                 64
  Cache size:                     32768
  Global memory size:                 8114036736
  Constant buffer size:                 65536
  Max number of constant args:             8
  Local memory type:                 Global
  Local memory size:                 32768
  Kernel Preferred work group size multiple:     1
  Error correction support:             0
  Unified memory for Host and Device:         1
  Profiling timer resolution:             1
  Device endianess:                 Little
  Available:                     Yes
  Compiler available:                 Yes
  Execution capabilities:                 
    Execute OpenCL kernels:             Yes
    Execute native function:             Yes
  Queue properties:                 
    Out-of-Order:                 No
    Profiling :                     Yes
  Platform ID:                     0x00007fda502abde0
  Name:                         Intel(R) Core(TM) i5-4590 CPU @ 3.30GHz
  Vendor:                     GenuineIntel
  Device OpenCL C version:             OpenCL C 1.2 
  Driver version:                 1445.5 (sse2,avx)
  Profile:                     FULL_PROFILE
  Version:                     OpenCL 1.2 AMD-APP (1445.5)
  Extensions:                     cl_khr_fp64 cl_amd_fp64 cl_khr_global_int32_base_atomics cl_khr_global_int32_extended_atomics cl_khr_local_int32_base_atomics cl_khr_local_int32_extended_atomics cl_khr_int64_base_atomics cl_khr_int64_extended_atomics cl_khr_3d_image_writes cl_khr_byte_addressable_store cl_khr_gl_sharing cl_ext_device_fission cl_amd_device_attribute_query cl_amd_vec3 cl_amd_printf cl_amd_media_ops cl_amd_media_ops2 cl_amd_popcnt cl_khr_spir cl_amd_svm cl_khr_gl_event 


  Platform Name:                 NVIDIA CUDA
Number of devices:                 1
  Device Type:                     CL_DEVICE_TYPE_GPU
  Vendor ID:                     10deh
  Max compute units:                 1
  Max work items dimensions:             3
    Max work items[0]:                 1024
    Max work items[1]:                 1024
    Max work items[2]:                 64
  Max work group size:                 1024
  Preferred vector width char:             1
  Preferred vector width short:             1
  Preferred vector width int:             1
  Preferred vector width long:             1
  Preferred vector width float:             1
  Preferred vector width double:         1
  Native vector width char:             1
  Native vector width short:             1
  Native vector width int:             1
  Native vector width long:             1
  Native vector width float:             1
  Native vector width double:             1
  Max clock frequency:                 705Mhz
  Address bits:                     64
  Max memory allocation:             134217728
  Image support:                 Yes
  Max number of images read arguments:         256
  Max number of images write arguments:         16
  Max image 2D width:                 16384
  Max image 2D height:                 16384
  Max image 3D width:                 4096
  Max image 3D height:                 4096
  Max image 3D depth:                 4096
  Max samplers within kernel:             32
  Max size of kernel argument:             4352
  Alignment (bits) of base address:         4096
  Minimum alignment (bytes) for any datatype:     128
  Single precision floating point capability
    Denorms:                     Yes
    Quiet NaNs:                     Yes
    Round to nearest even:             Yes
    Round to zero:                 Yes
    Round to +ve and infinity:             Yes
    IEEE754-2008 fused multiply-add:         Yes
  Cache type:                     Read/Write
  Cache line size:                 128
  Cache size:                     16384
  Global memory size:                 527826944
  Constant buffer size:                 65536
  Max number of constant args:             9
  Local memory type:                 Scratchpad
  Local memory size:                 49152
ERROR: clBuildProgram(-11)

```


As you can see my GPU is the second platform , hence in the main code i have selected "platform[1]"


So,
 The problem I am facing here is every time i compile my code
```

gcc main.c -l OpenCL



```

i am getting the error at the same line i.e at clBuildProgram() function which is returning the error code of -11.
And also the clGetProgramBuildInfo() fails to print the buildLog .

The output for the code I am getting everytime even with lots of tweaks :
```

$ ./a.out

 the total no. of platforms detected is :2

  Name of the platform selected: NVIDIA CUDA 
Device selected name is: Quadro 410 


no error in creatng context

 no error in creating commandQueue

 no error in creating CL program from source

build pgm returns code:-11


Error in kernel BUILD PGM: 
 
Error at: clCreateKernel(get kernel function failed)

 Error clEnqueueNDRangeKernel

Output is Incorrect



```

It would be very nice if anyone would be able to contribute their time and effort to bring forth the mistake I have done and not able to see.
Thank you.

---

### Post by soham-elessar on 2016-08-14
Try sending N to the kernel the same way you have sent the arrays. Inside the kernel you can access the value of N as N[0].

---

