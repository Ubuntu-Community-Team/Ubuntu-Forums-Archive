---
title: "What's the difference between Ubuntu 12.04.0,12.04.1,etc?"
date: 2015-11-19
forum: New to Ubuntu
---

### Post by remmas-sido on 2015-11-19
Hello, 
What's the difference between Ubuntu 12.04.0,12.04.1,etc...? 
this question also apply to 14.04.0,14.04.1,etc....
and can I install Ubuntu 12.04.0 and upgrade to 12.04.5?
this question also apply to 12.04.1,12.04.2,12.04.3,etc....
and will there be a 12.04.6 in the near future? if not then why? 
Thank you

---

### Post by deadflowr on 2015-11-19
12.04 > 12.04.1 = bug fixes
12.04.1 > 12.04.2 = bugs fixes + new hardware stack (kernel version and xserver packages) come with the installation iso. (it comes with the 12.10 hardware stack)
12.04.2 > 12.04.3 = same thing as above, but with a newer hardware stack on the new installation iso (it comes with the 13.04 hardware stack)
12.04.3 > 12.04.4 = same thing as the previous two, with, of course, a newer hardware stack on the installation iso. (it comes with the 13.10 hardware stack)
12.04.4 > 12.04.5 = same thing, but this is last one. (it comes with the 14.04 hardware stack)

From an updating point of view, if you where to install 12.04.0( or 12.04.1 or .2 or .3) or .4) your first update would move you to 12.04.5 but without the new hardware stack.

Same thing applies to 14.04.

Seems weird but makes sense if read about it's reasoning here: [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

---

### Post by grahammechanical on 2015-11-19
They are called Point releases because of the second dot or point after the .04.

As we know, a Long Term Support (LTS) release is supported for 5 years. But if we think about it, we may reason that an OS released in April 2012 will not be compatible with hardware released in 2013 or later. Linux is constantly being developed to keep up to date with the latest hardware. The point releases bring into the LTS release the latest Linux kernels and hardware modules.

So, if we were to  install Ubuntu 12.04 (12.04.0) on 2014 hardware we might find that it is not compatible with the hardware but Ubuntu 12.04.4 is compatible. Point releases are a way of keeping a version of Ubuntu supported for 5 years relevant with newer hardware.

This support has a cost for Canonical in the amount of time its paid employees have to spend producing these point releases. And then there is the cost of keeping the original kernels in 12.04 up to date with bug fixes for 5 years.

So, there is a limit to the number of point releases. And that limit seems to be reached a little over 2 years after release day. By which time there is a new Ubuntu LTS release available. I do not think it unreasonable to say if you want to install Ubuntu on the latest hardware then you should install the latest LTS release of Ubuntu and not a 2 year old release. We do not need a Ubuntu 12.04.6 because we have Ubuntu 14.04 (LTS) with its own point releases and in six months time there will be a Ubuntu 16.04 (LTS).

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

Regards.

---

### Post by michael2009 on 2015-11-20
Just a note on ubuntu 12.04. It is still popular with many people. It appears that some people prefer the 12.04 Desktop Environment, maybe because they got used to it and liked it, and didn't want to have to get used to a newer and different one with 14.04? As an older person, I can understand that point of view.

---

### Post by Geoffrey_Arndt on 2015-11-20
Uhh, it's the same desktop environment.   Windows may have differences between 7 8 10, but Ubuntu has been pretty stable if you're running the Unity desktop.    If you're running Xubuntu or Lubuntu, then of course it's different.

---

