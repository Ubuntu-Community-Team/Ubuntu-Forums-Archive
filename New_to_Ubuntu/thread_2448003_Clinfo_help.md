---
title: "Clinfo help"
date: 2020-07-30
forum: New to Ubuntu
---

### Post by indeedhappy80 on 2020-07-30
jr@jr-X299-UD4-Pro:~$ clinfo
Number of platforms                              2
  Platform Name                                  NVIDIA CUDA
  Platform Vendor                                NVIDIA Corporation
  Platform Version                                OpenCL 1.2 CUDA 11.0.197
  Platform Profile                                FULL_PROFILE
  Platform Extensions                             cl_khr_global_int32_base_atomics cl_khr_global_int32_extended_atomics  cl_khr_local_int32_base_atomics cl_khr_local_int32_extended_atomics  cl_khr_fp64 cl_khr_byte_addressable_store cl_khr_icd cl_khr_gl_sharing  cl_nv_compiler_options cl_nv_device_attribute_query cl_nv_pragma_unroll  cl_nv_copy_opts cl_nv_create_buffer cl_khr_int64_base_atomics  cl_khr_int64_extended_atomics
  Platform Extensions function suffix            NV

  Platform Name                                  Intel(R) CPU Runtime for OpenCL(TM) Applications
  Platform Vendor                                Intel(R) Corporation
  Platform Version                                OpenCL 2.1 LINUX
  Platform Profile                                FULL_PROFILE
  Platform Extensions                            cl_khr_icd  cl_khr_global_int32_base_atomics cl_khr_global_int32_extended_atomics  cl_khr_local_int32_base_atomics cl_khr_local_int32_extended_atomics  cl_khr_byte_addressable_store cl_khr_depth_images cl_khr_3d_image_writes  cl_intel_exec_by_local_thread cl_khr_spir cl_khr_fp64  cl_khr_image2d_from_buffer cl_intel_vec_len_hint 
  Platform Host timer resolution                  1ns
  Platform Extensions function suffix            INTEL

  Platform Name                                  NVIDIA CUDA
Number of devices                                2
  Device Name                                    GeForce RTX 2080 Ti
  Device Vendor                                  NVIDIA Corporation
  Device Vendor ID                                0x10de
  Device Version                                  OpenCL 1.2 CUDA
  Driver Version                                  450.51.05
  Device OpenCL C Version                        OpenCL C 1.2 
  Device Type                                    GPU
  Device Topology (NV)                            PCI-E, 01:00.0
  Device Profile                                  FULL_PROFILE
  Device Available                                Yes
  Compiler Available                              Yes
  Linker Available                                Yes
  Max compute units                              68
  Max clock frequency                            1635MHz
  Compute Capability (NV)                        7.5
  Device Partition                                (core)
    Max number of sub-devices                    1
    Supported partition types                    None
    Supported affinity domains                    (n/a)
  Max work item dimensions                        3
  Max work item sizes                            1024x1024x64
  Max work group size                            1024
  Preferred work group size multiple              32
  Warp size (NV)                                  32
  Preferred / native vector sizes                
    char                                                1 / 1      
    short                                                1 / 1      
    int                                                  1 / 1      
    long                                                1 / 1      
    half                                                0 / 0        (n/a)
    float                                                1 / 1      
    double                                              1 / 1        (cl_khr_fp64)
  Half-precision Floating-point support          (n/a)
  Single-precision Floating-point support        (core)
    Denormals                                    Yes
    Infinity and NANs                            Yes
    Round to nearest                              Yes
    Round to zero                                Yes
    Round to infinity                            Yes
    IEEE754-2008 fused multiply-add              Yes
    Support is emulated in software              No
    Correctly-rounded divide and sqrt operations  Yes
  Double-precision Floating-point support        (cl_khr_fp64)
    Denormals                                    Yes
    Infinity and NANs                            Yes
    Round to nearest                              Yes
    Round to zero                                Yes
    Round to infinity                            Yes
    IEEE754-2008 fused multiply-add              Yes
    Support is emulated in software              No
  Address bits                                    64, Little-Endian
  Global memory size                              11551440896 (10.76GiB)
  Error Correction support                        No
  Max memory allocation                          2887860224 (2.69GiB)
  Unified memory for Host and Device              No
  Integrated memory (NV)                          No
  Minimum alignment for any data type            128 bytes
  Alignment of base address                      4096 bits (512 bytes)
  Global Memory cache type                        Read/Write
  Global Memory cache size                        2228224 (2.125MiB)
  Global Memory cache line size                  128 bytes
  Image support                                  Yes
    Max number of samplers per kernel            32
    Max size for 1D images from buffer            268435456 pixels
    Max 1D or 2D image array size                2048 images
    Max 2D image size                            32768x32768 pixels
    Max 3D image size                            16384x16384x16384 pixels
    Max number of read image args                256
    Max number of write image args                32
  Local memory type                              Local
  Local memory size                              49152 (48KiB)
  Registers per block (NV)                        65536
  Max number of constant args                    9
  Max constant buffer size                        65536 (64KiB)
  Max size of kernel argument                    4352 (4.25KiB)
  Queue properties                                
    Out-of-order execution                        Yes
    Profiling                                    Yes
  Prefer user sync for interop                    No
  Profiling timer resolution                      1000ns
  Execution capabilities                          
    Run OpenCL kernels                            Yes
    Run native kernels                            No
    Kernel execution timeout (NV)                No
  Concurrent copy and kernel execution (NV)      Yes
    Number of async copy engines                  3
  printf() buffer size                            1048576 (1024KiB)
  Built-in kernels                                (n/a)
  Device Extensions                               cl_khr_global_int32_base_atomics cl_khr_global_int32_extended_atomics  cl_khr_local_int32_base_atomics cl_khr_local_int32_extended_atomics  cl_khr_fp64 cl_khr_byte_addressable_store cl_khr_icd cl_khr_gl_sharing  cl_nv_compiler_options cl_nv_device_attribute_query cl_nv_pragma_unroll  cl_nv_copy_opts cl_nv_create_buffer cl_khr_int64_base_atomics  cl_khr_int64_extended_atomics

  Device Name                                    GeForce RTX 2080 Ti
  Device Vendor                                  NVIDIA Corporation
  Device Vendor ID                                0x10de
  Device Version                                  OpenCL 1.2 CUDA
  Driver Version                                  450.51.05
  Device OpenCL C Version                        OpenCL C 1.2 
  Device Type                                    GPU
  Device Topology (NV)                            PCI-E, 02:00.0
  Device Profile                                  FULL_PROFILE
  Device Available                                Yes
  Compiler Available                              Yes
  Linker Available                                Yes
  Max compute units                              68
  Max clock frequency                            1635MHz
  Compute Capability (NV)                        7.5
  Device Partition                                (core)
    Max number of sub-devices                    1
    Supported partition types                    None
    Supported affinity domains                    (n/a)
  Max work item dimensions                        3
  Max work item sizes                            1024x1024x64
  Max work group size                            1024
  Preferred work group size multiple              32
  Warp size (NV)                                  32
  Preferred / native vector sizes                
    char                                                1 / 1      
    short                                                1 / 1      
    int                                                  1 / 1      
    long                                                1 / 1      
    half                                                0 / 0        (n/a)
    float                                                1 / 1      
    double                                              1 / 1        (cl_khr_fp64)
  Half-precision Floating-point support          (n/a)
  Single-precision Floating-point support        (core)
    Denormals                                    Yes
    Infinity and NANs                            Yes
    Round to nearest                              Yes
    Round to zero                                Yes
    Round to infinity                            Yes
    IEEE754-2008 fused multiply-add              Yes
    Support is emulated in software              No
    Correctly-rounded divide and sqrt operations  Yes
  Double-precision Floating-point support        (cl_khr_fp64)
    Denormals                                    Yes
    Infinity and NANs                            Yes
    Round to nearest                              Yes
    Round to zero                                Yes
    Round to infinity                            Yes
    IEEE754-2008 fused multiply-add              Yes
    Support is emulated in software              No
  Address bits                                    64, Little-Endian
  Global memory size                              11554717696 (10.76GiB)
  Error Correction support                        No
  Max memory allocation                          2888679424 (2.69GiB)
  Unified memory for Host and Device              No
  Integrated memory (NV)                          No
  Minimum alignment for any data type            128 bytes
  Alignment of base address                      4096 bits (512 bytes)
  Global Memory cache type                        Read/Write
  Global Memory cache size                        2228224 (2.125MiB)
  Global Memory cache line size                  128 bytes
  Image support                                  Yes
    Max number of samplers per kernel            32
    Max size for 1D images from buffer            268435456 pixels
    Max 1D or 2D image array size                2048 images
    Max 2D image size                            32768x32768 pixels
    Max 3D image size                            16384x16384x16384 pixels
    Max number of read image args                256
    Max number of write image args                32
  Local memory type                              Local
  Local memory size                              49152 (48KiB)
  Registers per block (NV)                        65536
  Max number of constant args                    9
  Max constant buffer size                        65536 (64KiB)
  Max size of kernel argument                    4352 (4.25KiB)
  Queue properties                                
    Out-of-order execution                        Yes
    Profiling                                    Yes
  Prefer user sync for interop                    No
  Profiling timer resolution                      1000ns
  Execution capabilities                          
    Run OpenCL kernels                            Yes
    Run native kernels                            No
    Kernel execution timeout (NV)                Yes
  Concurrent copy and kernel execution (NV)      Yes
    Number of async copy engines                  3
  printf() buffer size                            1048576 (1024KiB)
  Built-in kernels                                (n/a)
  Device Extensions                               cl_khr_global_int32_base_atomics cl_khr_global_int32_extended_atomics  cl_khr_local_int32_base_atomics cl_khr_local_int32_extended_atomics  cl_khr_fp64 cl_khr_byte_addressable_store cl_khr_icd cl_khr_gl_sharing  cl_nv_compiler_options cl_nv_device_attribute_query cl_nv_pragma_unroll  cl_nv_copy_opts cl_nv_create_buffer cl_khr_int64_base_atomics  cl_khr_int64_extended_atomics

  Platform Name                                  Intel(R) CPU Runtime for OpenCL(TM) Applications
Number of devices                                1
  Device Name                                    Intel(R) Core(TM) i5-7640X CPU @ 4.00GHz
  Device Vendor                                  Intel(R) Corporation
  Device Vendor ID                                0x8086
  Device Version                                  OpenCL 2.1 (Build 0)
  Driver Version                                  18.1.0.0920
  Device OpenCL C Version                        OpenCL C 2.0 
  Device Type                                    CPU
  Device Profile                                  FULL_PROFILE
  Device Available                                Yes
  Compiler Available                              Yes
  Linker Available                                Yes
  Max compute units                              4
  Max clock frequency                            4000MHz
  Device Partition                                (core)
    Max number of sub-devices                    4
    Supported partition types                    by counts, equally, by names (Intel)
    Supported affinity domains                    (n/a)
  Max work item dimensions                        3
  Max work item sizes                            8192x8192x8192
  Max work group size                            8192
  Preferred work group size multiple              <getWGsizes:1171: create context : error -2>
  Max sub-groups per work group                  1
  Preferred / native vector sizes                
    char                                                1 / 32      
    short                                                1 / 16      
    int                                                  1 / 8      
    long                                                1 / 4      
    half                                                0 / 0        (n/a)
    float                                                1 / 8      
    double                                              1 / 4        (cl_khr_fp64)
  Half-precision Floating-point support          (n/a)
  Single-precision Floating-point support        (core)
    Denormals                                    Yes
    Infinity and NANs                            Yes
    Round to nearest                              Yes
    Round to zero                                No
    Round to infinity                            No
    IEEE754-2008 fused multiply-add              No
    Support is emulated in software              No
    Correctly-rounded divide and sqrt operations  No
  Double-precision Floating-point support        (cl_khr_fp64)
    Denormals                                    Yes
    Infinity and NANs                            Yes
    Round to nearest                              Yes
    Round to zero                                Yes
    Round to infinity                            Yes
    IEEE754-2008 fused multiply-add              Yes
    Support is emulated in software              No
  Address bits                                    64, Little-Endian
  Global memory size                              16730038272 (15.58GiB)
  Error Correction support                        No
  Max memory allocation                          4182509568 (3.895GiB)
  Unified memory for Host and Device              Yes
  Shared Virtual Memory (SVM) capabilities        (core)
    Coarse-grained buffer sharing                Yes
    Fine-grained buffer sharing                  Yes
    Fine-grained system sharing                  Yes
    Atomics                                      Yes
  Minimum alignment for any data type            128 bytes
  Alignment of base address                      1024 bits (128 bytes)
  Preferred alignment for atomics                
    SVM                                          64 bytes
    Global                                        64 bytes
    Local                                        0 bytes
  Max size for global variable                    65536 (64KiB)
  Preferred total size of global vars            65536 (64KiB)
  Global Memory cache type                        Read/Write
  Global Memory cache size                        262144 (256KiB)
  Global Memory cache line size                  64 bytes
  Image support                                  Yes
    Max number of samplers per kernel            480
    Max size for 1D images from buffer            261406848 pixels
    Max 1D or 2D image array size                2048 images
    Base address alignment for 2D image buffers  64 bytes
    Pitch alignment for 2D image buffers          64 pixels
    Max 2D image size                            16384x16384 pixels
    Max 3D image size                            2048x2048x2048 pixels
    Max number of read image args                480
    Max number of write image args                480
    Max number of read/write image args          480
  Max number of pipe args                        16
  Max active pipe reservations                    65535
  Max pipe packet size                            1024
  Local memory type                              Global
  Local memory size                              32768 (32KiB)
  Max number of constant args                    480
  Max constant buffer size                        131072 (128KiB)
  Max size of kernel argument                    3840 (3.75KiB)
  Queue properties (on host)                      
    Out-of-order execution                        Yes
    Profiling                                    Yes
    Local thread execution (Intel)                Yes
  Queue properties (on device)                    
    Out-of-order execution                        Yes
    Profiling                                    Yes
    Preferred size                                4294967295 (4GiB)
    Max size                                      4294967295 (4GiB)
  Max queues on device                            4294967295
  Max events on device                            4294967295
  Prefer user sync for interop                    No
  Profiling timer resolution                      1ns
  Execution capabilities                          
    Run OpenCL kernels                            Yes
    Run native kernels                            Yes
    Sub-group independent forward progress        No
    IL version                                    SPIR-V_1.0
    SPIR versions                                1.2
  printf() buffer size                            1048576 (1024KiB)
  Built-in kernels                                (n/a)
  Device Extensions                              cl_khr_icd  cl_khr_global_int32_base_atomics cl_khr_global_int32_extended_atomics  cl_khr_local_int32_base_atomics cl_khr_local_int32_extended_atomics  cl_khr_byte_addressable_store cl_khr_depth_images cl_khr_3d_image_writes  cl_intel_exec_by_local_thread cl_khr_spir cl_khr_fp64  cl_khr_image2d_from_buffer cl_intel_vec_len_hint 


NULL platform behavior
  clGetPlatformInfo(NULL, CL_PLATFORM_NAME, ...)  No platform
  clGetDeviceIDs(NULL, CL_DEVICE_TYPE_ALL, ...)  No platform
  clCreateContext(NULL, ...) [default]            No platform
  clCreateContext(NULL, ...) [other]              Success [NV]
  clCreateContextFromType(NULL, CL_DEVICE_TYPE_DEFAULT)  No platform
  clCreateContextFromType(NULL, CL_DEVICE_TYPE_CPU)  No devices found in platform
  clCreateContextFromType(NULL, CL_DEVICE_TYPE_GPU)  No platform
  clCreateContextFromType(NULL, CL_DEVICE_TYPE_ACCELERATOR)  No devices found in platform
  clCreateContextFromType(NULL, CL_DEVICE_TYPE_CUSTOM)  Invalid device type for platform
  clCreateContextFromType(NULL, CL_DEVICE_TYPE_ALL)  No platform
NOTE: your OpenCL library only supports OpenCL 2.0,
but some installed platforms support OpenCL 2.1.
Programs using 2.1 features may crash
or behave unexpectedly





I CANT SEE ANYTHING WRONG WITH MY SYSTEM

---

### Post by indeedhappy80 on 2020-07-30
Need help with the following:

* Device #2: WARNING! Kernel exec timeout is not disabled.
             This may cause "CL_OUT_OF_RESOURCES" or related errors.
             To disable the timeout, see: [https://hashcat.net/q/timeoutpatch](https://hashcat.net/q/timeoutpatch)
* Device #4: WARNING! Kernel exec timeout is not disabled.
             This may cause "CL_OUT_OF_RESOURCES" or related errors.
             To disable the timeout, see: [https://hashcat.net/q/timeoutpatch](https://hashcat.net/q/timeoutpatch)
clCreateContext(): CL_DEVICE_NOT_AVAILABLE

---

