---
title: "CUDA: Problem compiling NVCC output file with g++"
date: 2012-08-27
forum: Programming Talk
---

### Post by eldudorinio on 2012-08-27
Hi everyone,

I have recently started with nVidia CUDA and I have some issues.

I have installed CUDA 4.2 on Lubuntu 12.04 (64-bit). Everything seems to be in place, as the SDK examples were compiled and run successfully. I did not run all examples, but the ones I tried were OK.

I have successfully compiled a .cu file with the following command:
```
$ nvcc -c -o cuda.o programName.cu
```

After that I tried compiling cuda.o with g++ (using g++ (Ubuntu/Linaro 4.4.7-1ubuntu2) 4.4.7) using the following command. Also adding the output:
```
$ g++ -o b cuda.o 
cuda.o: In function `__cudaUnregisterBinaryUtil()':
tmpxft_000007ae_00000000-1_programName.cudafe1.cpp:(.text+0x878): undefined reference to `__cudaUnregisterFatBinary'
cuda.o: In function `__sti____cudaRegisterAll_48_tmpxft_000007ae_00000000_4_programName_cpp1_ii_**number**()':
tmpxft_000007ae_00000000-1_programName.cudafe1.cpp:(.text+0x888): undefined reference to `__cudaRegisterFatBinary'
collect2: ld returned 1 exit status
```
_Note:_
**number** --> integer in programName.cu

If any additional information is required, let me know.

Can anyone help on this?

---

### Post by steeldriver on 2012-08-27
Well I imagine you will need to add at least the cuda lib (and perhaps a bunch of other subsidiary libs) on the link command line

```
g++ -o b cuda.o -lcuda -l???
```Maybe have a look in the Makefile(s) for the examples that built successfully and see what the link phase for those looks like (lib directives of the form -lcuda -lwhatever plus any -L/path/to/lib library paths)

I see you are into the whole brevity thing with your executable name

---

### Post by eldudorinio on 2012-08-30
Hey steeldriver, I'm sorry it took so long for me to reply. I saw your reply from day one, but I am currently caught up with another part of the code.

You must be right, I have included no CUDA libraries in my code and that must be the reason for the messages. 

I will post back here when I try to compile the CUDA code again.

Brevity, on the other hand, is an art :)

---

