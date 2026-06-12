---
title: "Cuda: toolkit installation"
date: 2012-09-09
forum: Programming Talk
---

### Post by abraxas334 on 2012-09-09
Hi,
I am using a computer with 3 nvidia graphic cards, but I am not sure if it has the cuda development toolkit installed. 
I tried running a simple hello world program and I get the following errors.
```


/tmp/tmpxft_00007b43_00000000-13_test.o: In function `main':
tmpxft_00007b43_00000000-1_test.cudafe1.cpp:(.text+0x7b): undefined reference to `cudaMalloc'
tmpxft_00007b43_00000000-1_test.cudafe1.cpp:(.text+0x8c): undefined reference to `cudaMalloc'
tmpxft_00007b43_00000000-1_test.cudafe1.cpp:(.text+0xa6): undefined reference to `cudaMemcpy'
tmpxft_00007b43_00000000-1_test.cudafe1.cpp:(.text+0xc0): undefined reference to `cudaMemcpy'
tmpxft_00007b43_00000000-1_test.cudafe1.cpp:(.text+0x11a): undefined reference to `cudaConfigureCall'
tmpxft_00007b43_00000000-1_test.cudafe1.cpp:(.text+0x14b): undefined reference to `cudaMemcpy'
tmpxft_00007b43_00000000-1_test.cudafe1.cpp:(.text+0x157): undefined reference to `cudaFree'
/tmp/tmpxft_00007b43_00000000-13_test.o: In function `__cudaUnregisterBinaryUtil()':
tmpxft_00007b43_00000000-1_test.cudafe1.cpp:(.text+0x17d): undefined reference to `__cudaUnregisterFatBinary'
/tmp/tmpxft_00007b43_00000000-13_test.o: In function `__device_stub__Z10add_arraysPcPi(char*, int*)':
tmpxft_00007b43_00000000-1_test.cudafe1.cpp:(.text+0x1a5): undefined reference to `cudaSetupArgument'
tmpxft_00007b43_00000000-1_test.cudafe1.cpp:(.text+0x1c4): undefined reference to `cudaSetupArgument'
/tmp/tmpxft_00007b43_00000000-13_test.o: In function `__sti____cudaRegisterAll_39_tmpxft_00007b43_00000000_4_test_cpp1_ii_4ffedce8()':
tmpxft_00007b43_00000000-1_test.cudafe1.cpp:(.text+0x221): undefined reference to `__cudaRegisterFatBinary'
tmpxft_00007b43_00000000-1_test.cudafe1.cpp:(.text+0x27f): undefined reference to `__cudaRegisterFunction'
/tmp/tmpxft_00007b43_00000000-13_test.o: In function `cudaError cudaLaunch<char>(char*)':
tmpxft_00007b43_00000000-1_test.cudafe1.cpp:(.text._Z10cudaLaunchIcE9cudaErrorPT_[cudaError cudaLaunch<char>(char*)]+0x14): undefined reference to `cudaLaunch'
collect2: ld returned 1 exit status


```

I have no administrative rights to the system, nor any experience with cuda. Does anyone know what the default installation path for the cuda toolkit would be, or how to test if it is properly installed?

Thanks for any help

---

### Post by dwhitney67 on 2012-09-09
The undefined reference issues mean one of two things:

1.  You did not specify a library (e.g. -lcuda);

2.  The library does not have an implementation for the functions spit out in the error messages.

Since my crystal ball is not working this weekend, I'm betting it is because of option 1 above.

P.S.  If after specifying the library, as in option 1, you get a different error indicating that the library cannot be found, then tell your system administrator to install it.

---

### Post by abraxas334 on 2012-09-11
Thanks for the reply! If i specify the library path I get the same error. 
My system admin is also not very helpful..
I'll work something out tho!

---

