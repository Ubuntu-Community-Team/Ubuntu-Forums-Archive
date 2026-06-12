---
title: "Ubuntu 14.04 slow sometimes"
date: 2015-12-28
forum: New to Ubuntu
---

### Post by cafeledavid on 2015-12-28
anyone have any idea why this runs slow sometimes for instance, just opening a folder with nothing else opened and after a reboot, just weird, thought it would be faster than windows 7 but win7 seems faster overall - brand new install of ubuntu 1 day ago

6GB RAM
Gallium 0.4 on AMD RS880
AMD Athlon(tm) II X2 240 Processor × 2

thanks

---

### Post by grahammechanical on 2015-12-28
> Gallium 0.4 on AMD RS880

That is the open source video driver. Have you tried a proprietary video driver for comparison? System Settings>Software & Updates>Additional Driver tab. We need to be connected to the internet and allow the utility time to find a selection of drivers.

Regards.

---

### Post by cafeledavid on 2015-12-28
thanks unfortunately no drivers found, i am assuming from your post the graphics driver is making it slow? i selected do not use open gl when logging into my desktop if that helps
actually for my first time login, i selected to use it but was slow too

i found this thread and looks like im SOL

[http://ubuntuforums.org/showthread.php?t=2181866](http://ubuntuforums.org/showthread.php?t=2181866)

[COLOR=#000000][INDENT]Sorry to tell you this, but AMD dropped Linux support for the AMD HD 2x/3x/4x-series chipsets starting with Ubuntu 12.04.2. To use the fglrx drivers, you have to be running an Ubuntu no newer than 12.04.1. The more recent versions use an X-server that is incompatible with the AMD fglx drivers for the HD 2x/3x/4x-series chipsets.[/INDENT]
[/COLOR]

---

### Post by Vladlenin5000 on 2015-12-28
Not much you can do about it. Standard Ubuntu with Unity but also Kubuntu and Ubuntu GNOME require powerful 3D acceleration that cannot be provided by the current state of affairs with the open source driver for your graphics.
Using a different DE will certainly improve performance and usability. Try Xubuntu or Lubuntu instead.

---

### Post by mörgæs on 2015-12-30
Just wanted to add that the open-source Radeon drivers are in a good condition, especially in 15.10, if you do not require 3D graphics. 

AMD supports developing open-source drivers for their GPUs and they evolve for each Buntu iteration.

---

