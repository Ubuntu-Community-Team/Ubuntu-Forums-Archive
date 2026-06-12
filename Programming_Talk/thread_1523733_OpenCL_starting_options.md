---
title: "OpenCL starting options?"
date: 2010-07-04
forum: Programming Talk
---

### Post by Black Sun on 2010-07-04
Hi all, I am a B.Tech student and our college is planning to setup a "mini" (;)) super computer and GPGPU is thought to be a viable solution to our problems. I searched the net for the same. I found it is possible using either CUDA, DirectCompute or OpenCL, out of which only OpenCL is cross platform, and i want to work in ubuntu only, so it seems the best option yet, but the problem is, it seems no one has ever tried to use OpenCL on ubuntu and/or i have not been able to find any useful resources.

I want to learn OpenCL as well as want to install a stable compiler/IDE for the same ( IBM provides a compiler for it but is hasn't been tested for ubuntu). 

Can somebody provide me with any links to resources?

---

### Post by pbrane on 2010-07-04
Have you looked at this?
[http://developer.nvidia.com/object/cuda_3_1_downloads.html#Linux]("http://developer.nvidia.com/object/cuda_3_1_downloads.html")

Compiling is done with *nvcc* which calls *gcc* to compile the code, not sure about an IDE, I use gedit and emacs.

P.S. I have installed the SDK and run OpenCL programs on Ubuntu, 10.04 I think, although it might have been 9.10. I removed the SDK because, if I remember correctly, one can't use the GPU if a GUI is already using the display. I had to run the apps in a VT after killing gdm. I wouldn't have used it enough to keep it, as I was really just trying it out. I needed it to work in a GUI anyway.

---

### Post by WRDN on 2010-07-04
I have an ATI 4870HD and can run the compatible OpenCL demos in Ubuntu. Demos such as those using OpenCL Images do not work, though that is because the card does not support them.

---

### Post by Black Sun on 2010-07-07
thanks&#12288;&#12354;&#12426;&#12364;&#12392;

---

