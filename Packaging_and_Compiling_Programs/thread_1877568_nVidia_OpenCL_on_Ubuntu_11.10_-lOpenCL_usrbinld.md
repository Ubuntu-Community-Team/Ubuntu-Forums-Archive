---
title: "nVidia OpenCL on Ubuntu 11.10 -lOpenCL /usr/bin/ld"
date: 2011-11-08
forum: Packaging and Compiling Programs
---

### Post by razvanc87 on 2011-11-08
Hello users,

I have an ASUS Notebook with nVidia gt 520m and thought about trying some OpenCL programming (first time) on Ubuntu 11.10. I installed the nvidia-current-dev package. Thus, I found libOpenCL.so and such in /usr/lib/nvidia-current/ folder:

```
$razvan@...:~$ locate libOpenCL.so
/usr/lib/nvidia-current/libOpenCL.so
/usr/lib/nvidia-current/libOpenCL.so.1
/usr/lib/nvidia-current/libOpenCL.so.1.0
/usr/lib/nvidia-current/libOpenCL.so.1.0.0
/usr/lib32/nvidia-current/libOpenCL.so
/usr/lib32/nvidia-current/libOpenCL.so.1
/usr/lib32/nvidia-current/libOpenCL.so.1.0
/usr/lib32/nvidia-current/libOpenCL.so.1.0.0
```

I then installed the CUDA Toolkit for Ubuntu 10.10 from nVidia website and also the NVIDIA GPU SDK (in /opt/gpu_sdk).

When I go to /opt/gpu_sdk/OpenCL and try the make command I get:

```
razvan@...:/opt/gpu_sdk/OpenCL$ make
make[1]: Entering directory `/opt/gpu_sdk/OpenCL/common'
a - obj/release/oclUtils.cpp.o
make[1]: Leaving directory `/opt/gpu_sdk/OpenCL/common'
make[1]: Entering directory `/opt/gpu_sdk/shared'
make[1]: Leaving directory `/opt/gpu_sdk/shared'
make -C src/oclConvolutionSeparable/
make[1]: Entering directory `/opt/gpu_sdk/OpenCL/src/oclConvolutionSeparable'
/usr/bin/ld: cannot find -lOpenCL
collect2: ld returned 1 exit status
make[1]: *** [../../..//OpenCL//bin//linux/release/oclConvolutionSeparable] Error 1
make[1]: Leaving directory `/opt/gpu_sdk/OpenCL/src/oclConvolutionSeparable'
make: *** [src/oclConvolutionSeparable/Makefile.ph_build] Error 2
```

Afeter installing the nvidia-current-dev package I went to /etc/ld.so.conf.d/ and made nvidia-current.conf where I specified /usr/lib/nvidia-current and /usr/lib32/nvidia-current. Then I used ldconfig for caching the new locations.

Needless to say, it didn't work. I also appended the /usr/lib/nvidia-current and /usr/lib32/nvidia-current to the LD_LIBRARY_PATH environment variable in the hope of working... it did not work.

EIDT:
I found out that the correct variable in this case was LIBRARY_PATH, which is gcc / g++ related.

---

### Post by Optimus Yarnspinner on 2012-01-28
late replay, but would you mind telling me in a noob-friendly way how to set that 
/usr/lib/nvidia-current/ in that LIBRARY_PATH of g++?

i.e. which file to modify with that lines (.bashrc? oder something in /ld.so.conf.d/?) or what tell g++/gcc?

Thanks a lot.

---

### Post by MadCow108 on 2012-01-28
having this in your ~/.bashrc should do it:
```
export LIBRARY_PATH=/usr/lib/nvidia-current/:$LIBRARY_PATH
export LD_RUN_PATH=/usr/lib/nvidia-current/:$LD_RUN_PATH
export LD_LIBRARY_PATH=${LD_LIBRARY_PATH+$LD_LIBRARY_PATH:}/usr/lib/nvidia-current/
```

the last one is a bit more complicated as its the one used at runtime and it must handle LD_LIBRARY_PATH being empty before setting it.
(else you could end up with ":/path/" in the variable which is a security issue, it will load libraries from the current directory)

---

