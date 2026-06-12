---
title: "Low Low Low Spped on Dell inspiron 6400"
date: 2013-07-09
forum: New to Ubuntu
---

### Post by alirezagoodarzi on 2013-07-09
Hello
I am new with Linux.

I have a Dell Inspiron 6400 that works good with XP. newly I installed last version of ubuntu in a 10 Meg partition. But its so slow that I can not even start testing it. I click firefox and it takes 10-15 second to run it. Completely not normal.
Is there any suggestions?

Thanks

---

### Post by mastablasta on 2013-07-09
what is your CPU and what is your graphics chip?

please read this: [http://ubuntuforums.org/showthread.php?t=1422475](http://ubuntuforums.org/showthread.php?t=1422475)

you can copy and paste commands into temrinal and then copy and paste the results in your forum post.

XP is an operating system from 2001, Ubuntu is from 2013. While XP, 98, 95, 3.11 and DOS all run (sort off) on my computer the new OS such as windows 7 and windows 8 would run quite a bit slower.

---

### Post by 3rdalbum on 2013-07-09
I think you just need to install a graphics driver, if available. Or turn off transparency and animations if there is no good driver available. Or use Ubuntu 12.04 or any recent Xubuntu or Lubuntu.

If you tell us how much RAM you have and what your graphics card is, we can help more. Ubuntu requires 1 gig of RAM, maybe a little less, but Xubuntu and Lubuntu can get by with less still.

---

### Post by newb85 on 2013-07-09
It would help if we knew what graphics card you have

```
sudo lshw -C display
```

and what distribution of Ubuntu you're running

```
lsb_release -a
```

---

### Post by alirezagoodarzi on 2013-07-09
Thank you so much.
I will do all recomendations and let you know the results.
Thanks

---

### Post by codenameSQL on 2013-07-09
the specs I found for your dell are:


[LIST]
[*]Intel Core Duo T2400 / 5 Mb Cache / 1.83 GHz / 667 MHZ FSB
[*]15.4" Wide-screen XGA Display with Truelife
[*]120 Gb 5400 rpm Sata Hard Drive
[*]1 Gb DDR2 SDRAM / 553 MHZ
[*]256 Mb ATI Mobility Radeon X1400 Hyper memory
[*]Windows XP Media Center
[*]9 - Cell Battery
[/LIST]
[COLOR=#787777]


I'm similarly a newbie such as yourself, and also in the process of updating a few older XP systems... and I've burned a quite a few 'Buntu variants, installed, and tested them.  Ubuntu with the Unity desktop is going to be much more sluggish with your system.  you have a 64bit duo proc, but lower graphics and system RAM.  Ubuntu's Unity or Kubuntu's KDE, or even Gnome3 will all run (much) more sluggishly, though that descriptor is rather ambiguous based on personal views of 'speed'.   For me, I found Lubuntu with LXDE to be blazingly fast, just not as the same eye candy (though it is quite easy to give it a make-over).  A more aesthetically eye pleasing out of the box experience is ZorinOS lite, also based on 'buntu + LXDE.  Extremely snappy and responsive.  

Xubuntu based on XFCE is a great looking setup and should run fast on your current specs.  LinuxMint 13 also has an XFCE version.  

From my testing with a P4 system with 2G ram,  this is my Desktop Environment experience from fastest to slowest...

LXDE (amazingly fast)
XFCE (very fast)
MATE (very fast)
Cinnamon (smooth/acceptably fast)
Gnome2 (acceptable)
Gnome3 (sluggish)
Unity (sluggish)
Unity in 2D mode (better, but didn't care for it much)
KDE (the walking dead)

Yes, I did install/wipe/install/test all of those.  One killer aspect of Open Source is that experimentation is absolutely free with the cost being only your time and effort.

This is a link for LXDE tips/tweaks, but it has a graphical chart about memory usage in the various DE's.  I can't verify the numbers, but my on keyboard experience tends to reflect the higher mem usage with slower system response in  the exact order of that chart.
[http://lxlinux.com/](http://lxlinux.com/)

I'd suggest to forego Unity DE on your current system and try some of the others.   

You can try different DE's on your current system.  They all use the same underlying Ubuntu core and just color the GUI differently.

Here's a link showing how to try the XFCE DE (or change your Ubuntu into Xubuntu - mostly)
[https://sites.google.com/site/easylinuxtipsproject/alternative](https://sites.google.com/site/easylinuxtipsproject/alternative)

Anyway, just one newbie to another.. YMMV! These experts may be able to help you tweak Unity to get acceptable performance by your assessment, but it just wasn't a go for me on my two older machines.  Try some others... [/COLOR]

---

### Post by Kopkins on 2013-07-10
I did an install on an old computer of mine that had similar specifications and also originally ran XP. I found LXDE to be the best desktop environment for me. With so little RAM you can't let it get taken up by the desktop. When I used to use Unity it would run at about 500MB after boot. Which would be about half of your RAM, then stuff starts getting swapped when you open firefox, which I've seen take up to 300MB RAM when running. Add that together and you've said goodbye to any sort of multitasking. And the any sort or speed goes away. I would try LXDE or lubuntu. 

Good Luck,

Kopkins

---

### Post by mastablasta on 2013-07-10
> **codenameSQL said:**
> 256 Mb ATI Mobility Radeon X1400 Hyper memory



ah. see, now that explains it. AMD dropped support for this card. what the OP can do is install latest opensource drivers using PPA and see if that helps or use a non 3D accelerated desktop (LXDE, XFCE, Openbox, IceWM, E17, Mate... ).


PPA for upgradign opensource drivers - xorg edgers (read the notes and install instructions): [https://launchpad.net/~xorg-edgers/+archive/](https://launchpad.net/~xorg-edgers/+archive/)

---

### Post by Dennis N on 2013-07-10
More Dell 6400 possible options here:

[https://wiki.archlinux.org/index.php/Dell_Inspiron_6400](https://wiki.archlinux.org/index.php/Dell_Inspiron_6400)

It was available in many configurations. In those days, you had cafeteria style ordering - pick the processor, wireless card, graphics, etc. that you wanted.

---

### Post by mastablasta on 2013-07-10
> 
[LIST]
[*]128MB ATI Mobility Radeon X1300 with HyperMemory
[*]256MB ATI Mobility Radeon X1400 with Hypermemory
[*]256MB nVidia GeForce Go 7300 with TurboCache
[*]128MB Intel Graphics Media Accelerator 950
[/LIST]


xorg edgers might help with all these gpu chips that were available. maybe if it's nvidia chip there might be proprietary drivers available (but porbably not). if the maschine has intel GPU then Xubuntu or Lubuntu would work better. that GPU is really weak.

---

### Post by newb85 on 2013-07-10
> **Dennis N said:**
> More Dell 6400 possible options here:

[https://wiki.archlinux.org/index.php/Dell_Inspiron_6400](https://wiki.archlinux.org/index.php/Dell_Inspiron_6400)

It was available in many configurations. In those days, you had cafeteria style ordering - pick the processor, wireless card, graphics, etc. that you wanted.

Hence the lshw command I requested in post #4.

---

