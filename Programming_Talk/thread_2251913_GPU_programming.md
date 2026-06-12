---
title: "GPU programming"
date: 2014-11-07
forum: Programming Talk
---

### Post by AADAS on 2014-11-07
Do you how to use my video card(gtx 660M) for computing?And I don't want to install additional drivers.

---

### Post by QIII on 2014-11-07
Hello!

GPGPU generally requires the proprietary driver for the GPU and, in your case, you will likely need CUDA (or OpenCL).  GPGPU usually requires access to functionality that is not exposed to the open source developers.

A good place to start getting oriented might be gpgpu.org.

Developing software that can take best advantage of the unique power of GPUs is not trivial and GPGPU is not suitable for everything.

Best wishes though.  That stuff is very exciting.

---

### Post by AADAS on 2014-11-07
The last time when I install CUDA toolkit 6.5 I got graphics glitches and kernel freezes .How to proceed with cuda toolkit?

---

### Post by QIII on 2014-11-07
The best place I can recommend to look is NVIDIA's documentation.

For instance, [this]("http://docs.nvidia.com/cuda/cuda-getting-started-guide-for-linux/index.html#axzz3IQJR8jx1") gives the instructions for installation.

---

