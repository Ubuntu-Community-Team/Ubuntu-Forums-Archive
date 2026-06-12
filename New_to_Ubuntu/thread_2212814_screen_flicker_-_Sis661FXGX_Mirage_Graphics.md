---
title: "screen flicker - Sis661FX/GX Mirage Graphics"
date: 2014-03-23
forum: New to Ubuntu
---

### Post by leroy3 on 2014-03-23
Hi all,

I'm an absolute beginner - trying to test ubuntu on my parents old XP machine.

I am trying to test ubuntu by booting from DVD - it gets so far then i get a purple / black screen flickering on and off.  Can see the mouse pointer on the purple phase but nothing else.  Would this be a graphics error?  

After a while a message comes up and says that "graphics card could not be detected correctly, will need to configure these yourself" - after that I can't get anywhere and have to power off the machine at the button.

Machine is a Pentium 4 - 2.93Ghz, C drive: 3.55Gb, D drive: 3.55Gb, 1.21Gb Ram.   

Graphics appear to be on board only "Sis661FX/GX Mirage Graphics"

Apologies if this has already been asked before - spotted a thread that seemed to be about the graphics but it was all over my head! 

Many thanks

Leigh

---

### Post by Hodevah on 2014-03-23
```
lspci 
``````
 lspci -v 
``````
 lspci -v | less
```  This might also help ```
lshw -short | grep -i --color display  
```.   also, would you mind editing your post's title so as to make it more relevant. having a title such as the one your using does not much at all in terms of having people understand or have some foreknowledge on what the problem that your having is.

---

### Post by stalkingwolf on 2014-03-23
what version of buntu are you trying?  Is it a 32bit?  Might try lubuntu or xubuntu. also might try mint 13.  I have a system with similar specs that i have installed several different distros on all 32 bit with no problems.

---

### Post by coffeecat on 2014-03-23
This is your problem:

> **leroy3 said:**
> 
Graphics appear to be on board only "Sis661FX/GX Mirage Graphics"


SiS graphics are notorious for being difficult to set up in Linux. Unfortunately, it would appear that an update to the xserver introduced a bug in Ubuntu 12.04, if I am reading this thread correctly:

[http://ubuntuforums.org/showthread.php?t=2201518](http://ubuntuforums.org/showthread.php?t=2201518)

There are a few comments in that thread that might be helpful though.

I also found this, merely to illustrate the problems some experience with SiS graphics:

[http://namakutux.blogspot.co.uk/2011/11/linux-driver-for-661741760-pciagp-or.html](http://namakutux.blogspot.co.uk/2011/11/linux-driver-for-661741760-pciagp-or.html)

I don't recommend downloading the driver. It could be OK, but you need to be wary of random downloads even with Linux. And that blog post refers to obsolete versions of Ubuntu anyway, so their driver package may or may not work with recent versions.

Since you are new to Ubuntu, is there any chance of you finding a machine to use that is not encumbered with SiS graphics? You have enough to learn with a new operating system without giving yourself heartache over a video device that is unlikely ever to work well in Linux distros.

---

### Post by Impavidus on 2014-03-23
> **leroy3 said:**
> Machine is a Pentium 4 - 2.93Ghz, C drive: 3.55Gb, D drive: 3.55Gb, 1.21Gb Ram.
If these are in reality two partitions on the same drive they can be merged to a single 7.1GB partition, which is rather (but not impossibly) small for Ubuntu. Maybe you have a somewhat larger spare drive somewhere. Ubuntu can also be run from an external drive, provided your computer boots from usb.

But the first problem to solve is the graphics problem.

---

### Post by leroy3 on 2014-03-23
Thanks SO much everyone.  Didn't manage to succeed with ubuntu but previewed xubuntu 12.04.4 from DVD and it is a peach.  My parents are close to retirement and they just want the internet really so it shall be perfect for their needs.  It is lightning quick and a joy to use, exactly the opposite of XP on the machine currently!!  I shall install tomorrow and do away with XP.  I'll be glad to see the back of it, to be honest! Hopefully the install shall be plain sailing tomorrow.

Thanks so much for being friendly and so very helpful, to you all!  

Leigh

---

### Post by Hodevah on 2014-03-23
Doing away with Windows?! Good for you!  The more Linux, the merrier.     I did away with Windows too and am using 4 Linux/Gnu Distros on a quad-boot system.  I couldn't be happier to never see the back end of Windows ever again.

---

