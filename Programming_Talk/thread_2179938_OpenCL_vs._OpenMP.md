---
title: "OpenCL vs. OpenMP"
date: 2013-10-10
forum: Programming Talk
---

### Post by King Dude on 2013-10-10
What do you think is better, OpenCL or OpenMP, and why?

---

### Post by azzamite on 2013-10-10
You can't really compare them, they're both for different scenarios.

OpenCL allows you to parallelize in any kind of device: CPU, GPU, FPGA, etc. that's what it was made for,
is a little harder to learn but is more extensible and supports a lot of devices.

OpenMP is mostly for "trivial" paralelization, it mostly breaks for loops into [p]threads and that's it, the code
will compile even without it installed (but will not be paralelized)

---

### Post by ssam on 2013-10-11
OpenMP can (for certain algorithms) give decent multicore speed up for very little developer effort. It is just markup comments that let the compiler do the threading.

OpenCL can (for certain algorthms)  give large speed ups on GPUs but it requires the algorithms to be rewritten and so takes substantially more work.

---

### Post by King Dude on 2013-10-11
Is it possible to use both OpenMP and OpenCL to get the best of both worlds?

---

### Post by rchrd on 2013-10-12
OpenMP 4.0 is a lot more than trivial. And it incorporates a number of features for parallelization with attached processors.
[http://openmp.org](http://openmp.org)

However, it might be awhile until all compilers implement all the 4.0 features.

---

