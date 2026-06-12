---
title: "Cuda"
date: 2010-07-22
forum: Programming Talk
---

### Post by nebu on 2010-07-22
I use CUDA on my desktop for some of my programs. My desktop runs Ubuntu 9.04 and has a NVIDIA GPU, so I managed to do the installation after reading a few tutorials online.

However, I would like to continue editing my code on my laptop. The laptop runs Ubuntu 10.04 and this is the description of its GPU from lshw
```

*-display:0
             description: VGA compatible controller
             product: Mobile GM965/GL960 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 0c
             width: 64 bits
             clock: 33MHz
             capabilities: msi pm bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:29 memory:e4600000-e46fffff
             memory:d0000000-dfffffff(prefetchable) 
             ioport:4000(size=8)

```

How do I install CUDA on this machine? I cant seem to find any tutorials online on how to install it in machines which do not have a nvidia graphics chip?

Thanks for the help

---

### Post by cascade9 on 2010-07-22
You cant install CUDA on a machine without a nVidia 8XXX series or higher GPU. 

No way that it is going to work with an Intel GPU.

---

### Post by nebu on 2010-07-22
> **cascade9 said:**
> You cant install CUDA on a machine without a nVidia 8XXX series or higher GPU. 

No way that it is going to work with an Intel GPU.
are you sure??

i was reading on the nvidia forums that you can run it in some sort of emulation mode.... but the guys there dont say how to do that!

---

### Post by cascade9 on 2010-07-22
Ther might be a hack to make it work on Intel GPUs, but I doubt it. 

More likely that it would work on ATI, since Intel GPUs are always a few generations behind ATI/nVidia.

---

### Post by Queue29 on 2010-07-22
> **nebu said:**
> are you sure??

i was reading on the nvidia forums that you can run it in some sort of emulation mode.... but the guys there dont say how to do that!

Compile with **-deviceemu**

This will cause the program to start up a bunch of pthreads and utilize those as if they were individual cores, all on your cpu.

---

### Post by ssam on 2010-07-22
for cross platform GPU programming you want openCL rather than CUDA.

---

### Post by nebu on 2010-07-23
> **ssam said:**
> for cross platform GPU programming you want openCL rather than CUDA.
I looked around for opencl.... however I could not find anything on how to install it in ubuntu....

another problem is that I couldnt even find anything on their website which looked remotely similar to "get sdk"

so i dont know really.... do you have any idea how to install it in ubuntu 10.04 64bit?

---

