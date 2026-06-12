---
title: "I can't find the current_kernel_time() in the linux/time.h"
date: 2009-03-27
forum: Packaging and Compiling Programs
---

### Post by brian1125 on 2009-03-27
I want to use the current_kernel_time()or do_gettimeofday() in Ubuntu 8.0.4.2, to find the system time .

But use #include<linux/time.h> will get error messages in linux kernel 2.6.26.8 .

I use the google find the function is located at "linux/time.h".

But my "linux/time.h" content and in the network's "linux/time.h" content is not same.

By the way, i find the current_kernel_time()or do_gettimeofday() code in the kernel 2.6.26.8 source code i download located at /include/linux/kernel/time.c

After I compile the linux kernel 2.6.26.8, I thought the linux/time.h content should be the network's one.

I don't know why.

If you know what i ask solution tell me please please...

(by the way, i use the [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu) method to compile kernel)

---

