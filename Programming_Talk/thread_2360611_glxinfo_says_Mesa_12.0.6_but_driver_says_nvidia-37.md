---
title: "glxinfo says Mesa 12.0.6 but driver says nvidia-375..."
date: 2017-05-06
forum: Programming Talk
---

### Post by mslinklater on 2017-05-06
HI. I'm an experienced coder* and want to start doing some OpenGL on Ubuntu. I have a laptop with an NVidia 1060 and I have chosen to install the NVidia drivers in the 'Software & Updates' application. Problem is, when I run 'glxinfo' it says I'm running the Mesa libs. How do I get the system to use the NVidia OpenGL libs ?

Thanks.

* Experienced with OSX & Windows, but a newb with Linux.

---

### Post by #&amp;thj^% on 2017-05-06
Please see this: [http://docs.nvidia.com/cuda/cuda-installation-guide-linux/](http://docs.nvidia.com/cuda/cuda-installation-guide-linux/)

---

### Post by mslinklater on 2017-05-06
After half a day of uninstalling, installing,messing etc I've finally got my OpenGL driver problems sorted. I followed the instructions on this site, added the graphics drivers ppa and installed all the stuff they mention. Did a reboot and now I'm rocking OpenGL 4.5 on my NVidia 1060.

[https://rajat-osgyan.blogspot.co.uk/2016/04/how-to-install-latest-nvidia-drivers-on.html](https://rajat-osgyan.blogspot.co.uk/2016/04/how-to-install-latest-nvidia-drivers-on.html)

---

