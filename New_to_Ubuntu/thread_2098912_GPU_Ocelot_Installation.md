---
title: "GPU Ocelot Installation"
date: 2012-12-28
forum: New to Ubuntu
---

### Post by AmyPond on 2012-12-28
Hi, I’m new to CUDA and Ubuntu in general. I'm currently trying to install CUDA onto my laptop that does NOT have an NVIDIA GPU, and I know to do this I must use GPU Ocelot. I've been following along with the website that was recommended on the Ocelot site:
[http://barefeg.wordpress.com/2012/06/16/how-to-install-gpuocelot-in-ubuntu-12-04/#more-11](http://barefeg.wordpress.com/2012/06/16/how-to-install-gpuocelot-in-ubuntu-12-04/#more-11)

I keep getting an error when I try to install the CUDA drivers:

```
ERROR: Unable to load the kernel module ‘nvidia.ko’. This
 happens most frequently when this kernel module was built 
 against the wrong or improperly configured kernel sources, with a
 version of gcc that differs from the one used to build the
 target kernel, or if a driver such as rivafb, nvidiafb, or
 nouveau is present and prevents the NVIDIA kernel module from
 obtaining ownership of the NVIDIA graphics device(s), or NVIDIA
 GPU installed in this system is not supported by this NVIDIA 
 Linux graphics driver release.
```

I have blacklisted these drivers:
```
rivafb
nvidiafb
nouveau
vga16fb
rivatv
amd76x_edac
```

The gcc version I have (when I run gcc -v)
```
gcc versions 4.6.3
```

I’m running Ubuntu 12.04 and can only get the CUDA 5 package (which is actually what I need) that I chose to download for Ubuntu 11.10.

Is there any additional information that could help?

---

### Post by AmyPond on 2012-12-28
Haha~ Okay, I realized my issue was just me being unobservant and not the brightest bulb in the box. I was trying to install the drivers in a computer that doesn't have anything NVIDIA. With CUDA 5, it doesn't give you the option to *download* any specific part, you get all the information for the drivers, toolkit, and samples. When using the command 
```
sudo ./cuda_5.0.35_linux_32_ubuntu11.10-1.run
``` is when you choose what you want to install. What you're supposed to do is skip over driver installation, accept the toolkit installation, and it's your choice about the samples. Everything works now.

---

