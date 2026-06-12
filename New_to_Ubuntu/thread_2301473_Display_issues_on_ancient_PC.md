---
title: "Display issues on ancient PC"
date: 2015-11-02
forum: New to Ubuntu
---

### Post by Wyatt_H on 2015-11-02
Hey folks,

First time posting here, so I hope it's ok that I just use 'New to' and hope to get pointed to the right place. My boss gave me a really old PC to browse and do math stuff at my desk (machinist). It's an Intel box (D865GLC) with Intel Extreme Graphics 2. I expect it to be really slow, and that's ok, but I've got some specific issues that I'd like to solve. 

Firstly, when I boot up or return from sleep/hibernation, there's a big black stripe running through the middle of the background and the wallpaper is all pixellated.

[http://imgur.com/9CmQHBB](http://imgur.com/9CmQHBB)

When I select a new background it instantly fixes the stripe and pixellation, I can even go back to this image and it displays correctly. I'm under the impression that I have the correct enough drivers, but suspect something else is going on here. In addition to this issue, all of my screen effects like fades are really slow and I'd like to just turn them off. Any thoughts?

---

### Post by grahammechanical on 2015-11-02
We need to know the hardware specification of that machine including the video adapter and how much of its own memory it has. We also need to know the version of Ubuntu that you have installed or whether it is another one of the family of Ubuntu Linux distributions.

New versions of Ubuntu come with new proprietary video drivers that have often dropped support for older video cards. So, you will need an older or legacy proprietary video driver. Also, Ubuntu requires a video adapter that can do hardware accelerated 3D rendering. This is why you might be better off installing Xubuntu, Lubuntu or Ubuntu Mate. A lot will depend on the hardware specification of that machine.

Regards.

---

### Post by sudodus on 2015-11-02
Welcome to the Ubuntu Forums :-)

I suggest the same thing as *grahammechanical*. Please tell us those details about the computer and the version of Ubuntu!

Guessing from your description I think you should try UXA acceleration according to the following link

[Lubuntu/AdvancedMethods#Old_Intel_graphics](https://wiki.ubuntu.com/Lubuntu/AdvancedMethods#Old_Intel_graphics)

and I think that Lubuntu would work best (fastest) of the Ubuntu 'family flavours', because it has the lightest desktop environment. But when we know more about the computer, it will be easier to give relevant advice.

See also this link for more details about [Old hardware brought back to life](http://ubuntuforums.org/showthread.php?t=2130640)

---

### Post by Wyatt_H on 2015-11-02
Specifications off the machine:

Memory: 3.5GiB
Processor: Intel Pentium 4 CPU 2.80GHz
Graphics: Gallium 0.4 on llvmpipe (LLVM 3.6, 128 bits)
OS type: 32-bit

I'm using Ubuntu 14.04. Intel Extreme Graphics 2 is a shared video adapter as far as I can tell, and doesn't have its own memory.

---

### Post by grahammechanical on 2015-11-02
Gallium 0.4 on llvmpipe is the open source video driver that Ubuntu uses when it detects a video adapter that is incapable of running the Ubuntu Unity 3D user interface. At least it got you to a working desktop. It is supposed to give an approximation of Unity by using the CPU to do the rendering because the graphic adapter (GPU) cannot do it. It kind of explains the failure to render the desktop environment properly. Too much work for the CPU.

You most definitely will be better off using Lubuntu as like Xubuntu the desktop environment does not require a graphic adapter that can do 3D rendering. 

[URL="http://lubuntu.net/"]http://lubuntu.net/

[/URL]Regards

---

### Post by sudodus on 2015-11-03
+1

I run Lubuntu in a similar computer, and I use UXA acceleration to get good graphics. See post #3.

---

### Post by poorguy on 2015-11-03
i am using ubuntu mate on a dell b110 p4 3.0ghz and 2.0gb ram and intel integrated graphics and it runs great.

---

