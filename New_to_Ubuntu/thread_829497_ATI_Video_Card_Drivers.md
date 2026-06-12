---
title: "ATI Video Card Drivers"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by azurepancake on 2008-06-14
I am currently using the "Proprietary ATI accelerated graphics driver" for my Radeon x1600. I know that there are other drivers for ATI cards to use with Linux and I am curious which one would be better suited for me.

The reason why I am so curious is because I've been trying to get World of Warcraft to run with Wine just as well as it did on Windows. It runs decently without OpenGL, but not up to par with how it did on Windows XP.

I hear that it is recommended to use OpenGL, but when I use it I get nasty graphical output, which you can see here [http://spiraledoutward.blogspot.com/2008/06/linux-and-wine-incomplete.html](http://spiraledoutward.blogspot.com/2008/06/linux-and-wine-incomplete.html)

So I wonder if switching drivers would patch up this problem. I know there are the restricted drivers, drivers offered by ati.com and then the "fglrx" driver. Is there any major differences I should know between these?

Any input would be greatly appreciated.

Thank you

---

### Post by finer recliner on 2008-06-14
the proprietary driver, fglrx and the driver officially offered on ATI's website are all the same thing. This driver can be buggy, but will get the most performance out of your graphics card. 

the open source VESA driver, is more stable, but cant do anything that requires 3d-acceleration (most games require this). 

i recommended using the fglrx driver that is in the ubuntu repositories, it is the easiest to install and will get you better performance.

---

### Post by ChameleonDave on 2008-06-14
I'm an NVIDIA man, and know nothing of ATI, but I can recommend EnvyNG as a great 3D video card configuration utility.

---

### Post by azurepancake on 2008-06-14
Doh, so there all the same driver, just different methods of install I suppose.

It seems that NVIDIA is the way to go with Linux. I'll make sure my next card is a NVIDIA. Until then, I'll give Envy a shot, thanks!

---

