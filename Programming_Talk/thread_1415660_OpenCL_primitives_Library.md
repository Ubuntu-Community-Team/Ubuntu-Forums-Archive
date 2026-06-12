---
title: "OpenCL primitives Library"
date: 2010-02-25
forum: Programming Talk
---

### Post by Ultra Magnus on 2010-02-25
Hi,

I've been investigating the possibility of enhancing the performance of some the image processing code used in the project I'm working on by using openCL.

I was wondering if anyone knows if there is a library available that implements common low level signal/image processing functions such as ffts, convolutions, multi grid operators etc a bit like the intel performance primitives library (which we are currently using)?

James

---

### Post by pbrane on 2010-02-25
Look into the GNU Scientific Library ( gsl ). I use several fft and optimization functions from libgsl for analog signal processing. Not sure about the image processing capabilities though.

There is also libmagickcore2 and libmagick++2 for image processing. I have not used them so I don't know if they will work for you.

---

### Post by Ultra Magnus on 2010-02-25
> **pbrane said:**
> Look into the GNU Scientific Library ( gsl ). I use several fft and optimization functions from libgsl for analog signal processing. Not sure about the image processing capabilities though.

There is also libmagickcore2 and libmagick++2 for image processing. I have not used them so I don't know if they will work for you.

I think those libraries all use the CPU. I've been having a look at openCL because it enables general purpose programming on the GPU whilst not being tied to a specific vendor's hardware. The IPP library is pretty quick and optimised for intel CPUs but I've done a few (non-scientific) tests and I think that using the GPU could give me an additional speed boost.

James

---

### Post by pbrane on 2010-02-26
Sorry, I didn't clue in to the fact that you want to offload the image processing to the GPU. As far as I know GSL only uses the CPU. I don't know of any libs that would do this other than the one you are using. I agree that using the GPU would be faster. I think it will ultimately depend on the GPU. The main problem is that your code would only run on GPUs that support openCL.

---

