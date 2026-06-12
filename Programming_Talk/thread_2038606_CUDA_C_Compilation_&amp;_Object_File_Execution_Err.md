---
title: "CUDA C Compilation &amp; Object File Execution Error"
date: 2012-08-07
forum: Programming Talk
---

### Post by smith9876 on 2012-08-07
Hello everyone,
I am a beginner in CUDA - C and this is my very first post here. I need some help in compiling c code for CUDA. I wrote a simple program given below and after compiling I got few error messages mentioned below.

```

#include<stdio.h>
#include<cuda.h>

__global__ void kernel(void)
{
}

int main (void)
{
        kernel<<<1,1>>>();
        printf("Hello World!\n");
        return 0;
}

```

Compilation 1: head is the executable and when I tried to run it I got error message - permission denied. I am unable to understand this. 

```

[abc@xyz cuda_c]$ nvcc -c -o head hello_world.cu
[abc@xyz cuda_c]$ ./head

-bash: ./head: Permission denied

```

Compilation 2: In this compilation some files could not be found. 

```

[abc@xyz cuda_c]$ nvcc hello_world.cu

/usr/bin/ld: warning: libdl.so.2, needed by /opt/cuda-toolkit/bin/../lib/libcudart.so, not found (try using -rpath or -rpath-link)
/usr/bin/ld: warning: libpthread.so.0, needed by /opt/cuda-toolkit/bin/../lib/libcudart.so, not found (try using -rpath or -rpath-link)
/usr/bin/ld: warning: librt.so.1, needed by /opt/cuda-toolkit/bin/../lib/libcudart.so, not found (try using -rpath or -rpath-link)
/opt/cuda-toolkit/bin/../lib/libcudart.so: undefined reference to `pthread_create@GLIBC_2.1'
/opt/cuda-toolkit/bin/../lib/libcudart.so: undefined reference to `pthread_join@GLIBC_2.0'
/opt/cuda-toolkit/bin/../lib/libcudart.so: undefined reference to `sem_init@GLIBC_2.1'
/opt/cuda-toolkit/bin/../lib/libcudart.so: undefined reference to `sem_wait@GLIBC_2.1'
/opt/cuda-toolkit/bin/../lib/libcudart.so: undefined reference to `pthread_detach@GLIBC_2.0'
/opt/cuda-toolkit/bin/../lib/libcudart.so: undefined reference to `pthread_getspecific@GLIBC_2.0'
/opt/cuda-toolkit/bin/../lib/libcudart.so: undefined reference to `sem_post@GLIBC_2.1'
/opt/cuda-toolkit/bin/../lib/libcudart.so: undefined reference to `sem_trywait@GLIBC_2.1'
/opt/cuda-toolkit/bin/../lib/libcudart.so: undefined reference to `sem_timedwait@GLIBC_2.2'
/opt/cuda-toolkit/bin/../lib/libcudart.so: undefined reference to `pthread_mutexattr_init@GLIBC_2.0'
/opt/cuda-toolkit/bin/../lib/libcudart.so: undefined reference to `dlsym@GLIBC_2.0'
/opt/cuda-toolkit/bin/../lib/libcudart.so: undefined reference to `dlopen@GLIBC_2.1'
/opt/cuda-toolkit/bin/../lib/libcudart.so: undefined reference to `pthread_key_create@GLIBC_2.0'
/opt/cuda-toolkit/bin/../lib/libcudart.so: undefined reference to `sem_destroy@GLIBC_2.1'
/opt/cuda-toolkit/bin/../lib/libcudart.so: undefined reference to `pthread_setspecific@GLIBC_2.0'
/opt/cuda-toolkit/bin/../lib/libcudart.so: undefined reference to `pthread_key_delete@GLIBC_2.0'
/opt/cuda-toolkit/bin/../lib/libcudart.so: undefined reference to `dlclose@GLIBC_2.0'
/opt/cuda-toolkit/bin/../lib/libcudart.so: undefined reference to `pthread_mutexattr_settype@GLIBC_2.1'
collect2: error: ld returned 1 exit status

```

Could anybody please explain what am I doing wrong? Could anybody please give me some links to compile c code for cuda. I am confused here and any help would be greatly appreciated. Thanks!

Regards
smith

---

