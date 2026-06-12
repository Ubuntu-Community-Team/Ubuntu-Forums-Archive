---
title: "segmentation fault on devicequery(CUDA)"
date: 2012-09-10
forum: Programming Talk
---

### Post by llvll0hsen on 2012-09-10
When I am running the devicequey from CUDA SDK I'm getting segmentation fault error:

```





[deviceQuery] starting...

./deviceQuery Starting...

 CUDA Device Query (Runtime API) version (CUDART static linking)

Found 1 CUDA Capable device(s)

Device 0: "GeForce GTX 560 Ti"
  CUDA Driver Version / Runtime Version          4.2 / 4.0
  CUDA Capability Major/Minor version number:    2.1
  Total amount of global memory:                 1024 MBytes (1073283072 bytes)
  ( 0) Multiprocessors x ( 48) CUDA Cores/MP:    0 CUDA Cores
  GPU Clock rate:                                1660 MHz (1.66 GHz)
  Memory Clock rate:                             2004 Mhz
  Memory Bus Width:                              256-bit
  L2 Cache Size:                                 524288 bytes
  Max Texture Dimension Size (x,y,z)             1D=(65535), 2D=(2048,2048), 3D=(0,512,0)
  Max Layered Texture Size (dim) x layers        1D=(0) x 1, 2D=(0,0) x 0
  Total amount of constant memory:               65536 bytes
  Total amount of shared memory per block:       49152 bytes
  Total number of registers available per block: 32768
  Warp size:                                     32
  Maximum number of threads per multiprocessor:  32653
  Maximum number of threads per block:           1024
  Maximum sizes of each dimension of a block:    1024 x 1024 x 64
  Maximum sizes of each dimension of a grid:     65535 x 65535 x 65535
  Maximum memory pitch:                          2147483647 bytes
  Texture alignment:                             512 bytes
  Concurrent copy and execution:                 Yes with 1559316080 copy engine(s)
  Run time limit on kernels:                     Yes
  Integrated GPU sharing Host Memory:            No
  Support host page-locked memory mapping:       Yes
  Concurrent kernel execution:                   Yes
  Alignment requirement for Surfaces:            No
  Device has ECC support enabled:                Yes
  Device is using TCC driver mode:               Yes
  Device supports Unified Addressing (UVA):      Yes
  Device PCI Bus ID / PCI location ID:           1570935040 / 32653
  Compute Mode:
Segmentation fault


```

I re-installed cudatoolkit again but getting this error!? Also I dont know why I'm getting different verison of runtime and driver?

Any suggestion?
Thanks

---

