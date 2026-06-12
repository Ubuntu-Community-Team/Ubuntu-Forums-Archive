---
title: "C Undefined Function Error"
date: 2009-08-14
forum: Programming Talk
---

### Post by virati on 2009-08-14
I've got a multi-file project that I didn't write (I'm extending implementation to use CUDA) and after hours of finding the right libraries, compiler and linker options I started adding my own .cu file to the project.

I'm using Code::Blocks and it gives me an error - "undefined reference to cuda_setup()". If i place the actual function IN one of the files (any of them) that came with the project then I have no problem. However, the source file I added IS being compiled into an object.

How do I get the linker to link my object file into the executable? I'm not using a makefile, just sort of blindly letting code::blocks do its thing.

---

