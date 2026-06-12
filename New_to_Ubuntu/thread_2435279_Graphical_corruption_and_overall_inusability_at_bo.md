---
title: "Graphical corruption and overall inusability at boot while trying every ubuntu flavor"
date: 2020-01-18
forum: New to Ubuntu
---

### Post by punstar on 2020-01-18
Every time I try to boot into a bootable USB with any version of Ubuntu loaded in, as soon as the desktop background loads I'm greeted with graphical corruption and screen tearing on one monitor and total darkness on the other.

The ubuntu flavours I've tried were:

Xubuntu
Budgie
Lubuntu
Kubuntu
Ubuntu MATE
Ubuntu

They all show this issue after boot, except Kubuntu that is usable despite the fact navigating the Menu UI causes the graphical corruption and screen tearing to appear, if the Menu is closed it doesn't tend to appear as often.
I've tried redownloading, retorrenting and reinstalling into a USB each version at least 3 times each, and I've tried different USB keys. Nothing seems to fix this problem.
Problems started showing after I changed my graphics card from a 750ti to an AMD r9 390.

---

### Post by Impavidus on 2020-01-18
Sounds like a graphics driver problem. Which release have you tried? All Ubuntu flavours use the same kernel, so not much difference there. Kubuntu may have a different method of drawing the screen, which may make it less susceptible to your problem.

---

### Post by punstar on 2020-01-18
Each version I tested was 18.04.3 since that's the only version I saw supported on AMD's website.

---

### Post by oldfred on 2020-01-18
Do not know AMD, but found this:

[https://forum.level1techs.com/t/amd-r9-390-finally-usable-on-linux/131922](https://forum.level1techs.com/t/amd-r9-390-finally-usable-on-linux/131922)

---

### Post by mörgæs on 2020-01-18
Try to feed it a 19.10 ISO.

---

### Post by punstar on 2020-01-18
Sure, will the drivers still work for 19.10 though? I'm not very experienced but AMD's website only provides drivers for 18.04.3

---

### Post by kurt18947 on 2020-01-18
> **mörgæs said:**
> Try to feed it a 19.10 ISO.

I second morgaes recommendation, try 19.10. I'm not sure about your video card but can affirm that AMD Vega 8 graphics integral to Ryzen 2200G do not work on Ubuntu 18.04. I suspect your video card may be of a similar generation or newer. I installed 18.04 HWE kernel & Xorg, that's better but isn't a perfect solution. 19.10 live USB works as I would expect. I hope 20.04 will be as good or better than 19.10 in its support of cutting edge hardware.

---

### Post by mörgæs on 2020-01-18
Try 19.10 as it is without adding drivers from AMD or other sources.

---

### Post by punstar on 2020-01-18
I tried with 3 19.10 flavours, Kubuntu, Xubuntu and Ubuntu.
I still didn't see any improvement for the situation in Kubuntu or Ubuntu, Xubuntu held up for a while but every time I opened the menu it started glitching and if I moved windows a certain way both screens just went black.
I was able to install Xubuntu on my disk with enough fiddling around but it was the same as I described it in the main post, for the record I wasn't able to install any sort of drivers yet, and trying to check the "additional drivers" section just showed nothing so I'm on the assumption I'm just running on the standard display drivers.

---

### Post by NM5TF on 2020-01-18
to find out what drivers you are using, open a terminal &  post the output of 

```
inxi -G
```

you might also take a look here  [https://www.amd.com/en/support/kb/release-notes/rn-prorad-lin-18-20](https://www.amd.com/en/support/kb/release-notes/rn-prorad-lin-18-20)

it claims support for Ubuntu 18.04 and your card

tommy

---

### Post by punstar on 2020-01-19
I managed to run inxi -G but because I wasn't able to log into a browser before the OS corrupting the display again, all I could get was a quick picture of it, sorry for the crude way it was taken, it's just that I didn't expect to get that far after many restarts and still being able to get a picture, let alone a copy of the text.[IMG]https://imgur.com/a/zfN0z0U[/IMG][IMG]https://imgur.com/a/zfN0z0U[/IMG] One weird thing is that the 1280x1024 display is a 75hz display but it shows in the terminal as 60hz, everything else seems correct.

Photo hosted on imgur since it seems to take a lot of screen space in the forum
[https://imgur.com/a/zfN0z0U](https://imgur.com/a/zfN0z0U)

---

### Post by Impavidus on 2020-01-19
As a general rule, don't look for drivers on the manufacturer's website. Use the additional drivers utility instead. That should select the appropriate drivers and help you download and install them.

For AMD graphics drivers there was a change recently. For older kernels you have to install the proprietary drivers using the additional drivers utility, but for more recent kernels the AMD drivers are built-in. I don't know exactly at which kernel the change happened.

If you installed Ubuntu using the 18.04 or 18.04.1 iso (or any of the other flavours), you get kernel 4.15, which needs the proprietary drivers. The 18.04.3 iso comes with the HWE stack enabled and gives you kernel 5.0. Maybe that one still needs the proprietary drivers. But a few days ago 18.04 with HWE stack upgraded to kernel 5.3, which is the same as the one used on Ubuntu 19.10 and has the drivers built-in. I don't know about the quality of those drivers. For cutting-edge hardware they may be buggy.

So telling that Ubuntu 18.04 is supported is not very clear, as there is a difference between Ubuntu 18.04 with and without HWE stack. And telling that Ubuntu 18.04.3 (with HWE stack) is supported isn't very clear either, as 18.04.3 with HWE stack automatically upgrades to the next kernel, where support may be different.

When you installed 18.04.3, did you tell in to install upgrades right away? That may have given you a newer kernel (the one for Ubuntu 18.04.4), which would affect AMD's proprietary drivers.

You mention using two monitors. Do you get a usable system if you only connect one monitor?

---

### Post by punstar on 2020-01-19
For the record, I haven't been able to install any manufacturer drivers yet, I planned to use 18.04.3 because I was getting weird performance and same graphical instability in other distros and thought it might be fixed by getting official drivers installed, I don't seem to get far enough on a terminal or in the files manager to go an install them due to the problems I'm having so I'm just running with whatever default selection Xubuntu chose during installation, the additional drivers tells me there isn't additional drivers to be downloaded so I can't get anything off there, unless there is a way to do so.

Also I've tried to install and boot into the OS with 1 monitor each for a while but depending on the one I use It's just glitchiness (1280x1024 75hz) or just a black screen (1920x1080 60hz)

---

