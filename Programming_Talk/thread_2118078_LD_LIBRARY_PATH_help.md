---
title: "LD_LIBRARY_PATH help"
date: 2013-02-20
forum: Programming Talk
---

### Post by yellena on 2013-02-20
Hello!
I'm trying to configure certain program for GPU and for it i need CUDA and Intel Math Kernel Library. 
For some reason, every time I try to ./configure i get error.

```
configure: error: Please check if CUDA is correctly installed.
```or
```
configure: error: Please check if a valid BLAS library is correctly installed
```I found out I should modify environment variables when ever i start terminal. So I use:

```
export PATH=$PATH:/usr/local/cuda-5.0/bin
export LD_LIBRARY_PATH=/usr/local/cuda-5.0/lib64:/lib
export LD_LIBRARY_PATH=/opt/intel/mkl/lib/intel64
```But this calls just one of libraries, not both.
I'm preety new to Linux(as you probably noticed :) ), so I'm wondering if I'm doing something wrong? How can I call both libraries at the same time?
I'm using Ubuntu 12.04 LTS.

---

### Post by schragge on 2013-02-20
IIRC, LD_LIBRARY_PATH is used when you have a program that needs some libraries at the *run* time.
To specify libraries to be linked with for *compiler*, you should use LIBRARY_PATH instead.
[highlight]Edit.[/highlight]
Ah I see. Your second *export* overwrites the first one. Try
```

export LD_LIBRARY_PATH=/usr/local/cuda-5.0/lib64:/lib:/opt/intel/mkl/lib/intel64

```

---

### Post by yellena on 2013-02-20
Just tried, doesn't work, now I get CUDA error
```
configure: error: Please check if CUDA is correctly installed
```

---

### Post by MadCow108 on 2013-02-20
LD_LIBRARY_PATH is for runtime, configure normally checks compile time existance
usually the configure has some flag to define the location of its dependencies, e.g. --with-cuda=/usr/local/cuda-5.0/
check ./configure --help

the config.log is also helpful to see where exactly its failing.

---

### Post by yellena on 2013-02-22
I configure with:

```
./configure --with-cuda-dir=/usr/local/cuda-5.0/ --enable-multi-gpu
```
and before that i do 
```
export LD_LIBRARY_PATH=/opt/intel/mkl/lib/intel64
```

Here's my config.log

---

