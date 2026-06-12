---
title: "How to GPGPU in Linux?"
date: 2008-08-13
forum: Programming Talk
---

### Post by Envergure on 2008-08-13
What's the best way to employ GPGPU in Linux?

Another Q:  Will OpenCL be coming to Linux or is is set to be a Mac exclusive?

---

### Post by cprofitt on 2008-08-13
I know Nvidia has stuff for GPU programming in Linux -- [http://www.nvidia.com/object/cuda_get.html](http://www.nvidia.com/object/cuda_get.html)

From what I have ready OpenCL is very new and is Apple only at this time. I am not sure if it will catch on for other OSes or if Apple will truly make it open at this time.

---

### Post by neoncode on 2008-08-15
According to the [wikipedia article]("http://en.wikipedia.org/wiki/OpenCL") on OpenCL, apple proposed it to the Khronos Group. So Linux might see some sort of Open Source implementation? libopencl anyone? :)

Also, it says that AMD adopted it for their GPU's. Perhaps NVidia will abandon CUDA in favor of OpenCL. Or support both? It would be nice to see a platform independent implementation for programing GPGPU supported by all GPU's. Perhaps this is it?

---

### Post by bfhicks on 2008-09-12
Don't know if anyone is still checking this thread, but NVIDIA does offer CUDA for ubuntu releases. I just built the 7.10 nvidia driver offered on the site and it worked flawlessly on my 8.04 system.

---

### Post by aeacides on 2008-12-13
Do someone know if a desktop environment team or Canonical plans to implement OpenCL in their next realease ( eg: JJ )? Probably too early to say anything about this ... I'm just excited to know if my preferred OS / DE will benefit of GPGPU.

 :p

---

### Post by Sockerdrickan on 2008-12-13
> **Envergure said:**
> What's the best way to employ GPGPU in Linux?

Another Q:  Will OpenCL be coming to Linux or is is set to be a Mac exclusive?
OpenCL is a standard, it's already released.

Drivers will be available everywhere

---

### Post by Sockerdrickan on 2008-12-13
> **aeacides said:**
> Do someone know if a desktop environment team or Canonical plans to implement OpenCL in their next realease ( eg: JJ )? Probably too early to say anything about this ... I'm just excited to know if my preferred OS / DE will benefit of GPGPU.

 :p
It's up to developers such as nVidia and AMD.

---

### Post by disco1 on 2009-01-25
> **Tux0r said:**
> OpenCL is a standard, it's already released.

Drivers will be available everywhere

The first draft of the standard is released, there are currently no implementations available.

Apple will probably release the first implementation, hopefully NVidia will follow for both Linux and Windows.

---

### Post by ssam on 2009-01-26
you could look at [Gallium3D]("http://en.wikipedia.org/wiki/Gallium3D").

---

### Post by jespdj on 2009-01-26
I've recently [downloaded NVIDIA's CUDA SDK](http://www.nvidia.com/object/cuda_get.html). It's fairly easy to set up and to compile the demo programs that come with it. There are some cool demos, such as a Mandelbrot fractal program which computes the fractal live on your videocard, with the ability to zoom in etc.

---

### Post by KyleRaynor on 2009-09-29
New update for you, just saw this and your post today.
[http://developer.nvidia.com/object/opencl-download.html](http://developer.nvidia.com/object/opencl-download.html).
I hope you like.

---

### Post by Envergure on 2009-09-29
Hi, 

I forgot about this thread!  I'm in university now and they're forcing me to use Windows >:(

Cool post.  I haven't done any programming for a while.

---

### Post by KyleRaynor on 2009-09-30
I know the feeling. I couldn't even apply at one of our local banks unless I used Ie 5 or later ON a ms os. But strangely user agent switcher forced the site to let me use FF in ubuntu. I HATE sites that blindly require microsoft, especially those that don't really need it.

On a side note, I also hate sites that actually do require microsoft. Like netflix. There is NO way that they can't make it work in linux. They are half done, it already works in ff.

---

