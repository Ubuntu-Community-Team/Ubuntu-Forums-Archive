---
title: "Accessing GPU and Video RAM"
date: 2008-05-08
forum: Programming Talk
---

### Post by &amp;)ky#)^ on 2008-05-08
As a hobby project, I'm doing some unconventional graphics code.  More specifically, I'm rendering 3D objects without using polygons.  Everywhere I look online, the only way I see to do these types of things involves what's known as "software rendering" which is a complete misnomer, yet I digress.  Anyway, that just means that your CPU and regular RAM is doing all the hard work instead of the GPU and your video RAM.  Well, just because I'm not using polygons doesn't mean, IMHO, that the GPU and the video RAM should get to just stand around doing next to nothing.  All they end up doing is boring old blitting.  Then the problem is that the CPU is getting bogged down chugging away at a bunch of repetitive trigonometric functions while the GPU is sitting there twiddling its digits. (Nice pun, eh? ;)

So, that huge amount of backstory amounts to this relatively simple question.  How can I send instructions or calculations to the GPU instead of the CPU? And how can I store variables in video RAM over regular RAM?  I don't see why I can't do it.  The GPU is a processing unit after all and all of my equations are, at worst, geometric or trigonometric in nature.  That's what the GPU is there for, right?  And RAM is RAM.  Plus, the folks at [GPGPGPU]("http://www.gpgpgpu.com/") figured out how to use GPUs for alternative purposes.

Since this is so low-level, I'll probably want to use C or C++.  I don't want to have to touch assembly, though.  So, please help.  Tutorials are welcome and preferred.

---

### Post by &amp;)ky#)^ on 2008-05-08
I've done a little extra research mostly to hone my vocabulary in this field.  It looks like I'm wanting to learn to write shaders for more generic computation.

Anybody familiar with possible tutorials for shader development?  I'm as green as can be with shaders.

---

### Post by Wybiral on 2008-05-08
One such option (if it is an option for you) would be [Cuda]("http://www.nvidia.com/object/cuda_learn.html").

---

### Post by &amp;)ky#)^ on 2008-05-08
I'm afraid it's not an option.  I'm running an Intel integrated video chipset.  I know it sucks, but I'm on a laptop.

---

### Post by RIchard James13 on 2008-05-08
I don't know how to tell the processor what to do. Maybe you could look at the source code for the X driver. As for the memory well Linux can use it for swap here is an article that explains how.
[http://gentoo-wiki.com/TIP_Use_memory_on_video_card_as_swap]("http://gentoo-wiki.com/TIP_Use_memory_on_video_card_as_swap")

---

### Post by &amp;)ky#)^ on 2008-05-08
From my research, it looks like I'll either want to play around with GLSL or Cg.  My only problem is that all the tutorials I've found are for vertex shaders or pixel shaders.  I want to program [generic shaders]("http://en.wikipedia.org/wiki/Shader_(realtime%2C_logical)").  The end goal here is to get my GPU to crunch numbers for me similar to how a CPU might do so via its programmable pipeline.

---

### Post by samjh on 2008-05-08
> **bluej774 said:**
> From my research, it looks like I'll either want to play around with GLSL or Cg.  My only problem is that all the tutorials I've found are for vertex shaders or pixel shaders.  I want to program [generic shaders]("http://en.wikipedia.org/wiki/Shader_(realtime%2C_logical)").  The end goal here is to get my GPU to crunch numbers for me similar to how a CPU might do so via its programmable pipeline.

I'm not a specialist in this area.  However, my understanding is that on PCs, scene geometry is processed by the CPU, and shading and textures are processed by the GPU.

That doesn't mean you can't do what you want with your GPU. ;)

Take a look at these.
Sh (high-level general programming for GPUs): [http://libsh.org/](http://libsh.org/)
CUDA (from nVidia, not sure if Intel supports it): [http://www.nvidia.com/object/cuda_home.html](http://www.nvidia.com/object/cuda_home.html)
GPU programming tutorial: [http://www.vis.uni-stuttgart.de/vis03_tutorial/](http://www.vis.uni-stuttgart.de/vis03_tutorial/)

---

### Post by Quikee on 2008-05-08
To be able to program the GPU's generic shader (or stream processor) you need to have a specific API to access it (or framework like CUDA and whatever AMD/ATI has). 

In case of OpenGL 2.x you don't program a generic shader but a shader for the specific task (pixel/vertex/geometry), but the driver will use the generic shaders for either of the tasks. In GPU that don't support DirectX 10, you had only limited number of specific shaders.

Usually for programming GPGPU with OpenGL you use pixel shaders, and load data as a texture (or use SH / Brooke to hide this). I don't think there is some other way around this - at least until there is some unified GPGPU library/framework available (OpenGPGPU? ;) ). I don't know what OpenGL 3.0 will bring.. maybe it will be possible to do a more generic processing with it.

---

### Post by &amp;)ky#)^ on 2008-05-08
I've investigated Brook and Sh and it looks like they've pretty much been abandoned for commercial implementations.  So it looks like I'll be doing it the hard way with pixel shaders like Quikee mentioned.

Thanks for all the hints and tips.  You've all been life-savers.

---

