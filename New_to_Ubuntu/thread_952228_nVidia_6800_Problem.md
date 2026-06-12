---
title: "nVidia 6800 Problem"
date: 2008-10-18
forum: New to Ubuntu
---

### Post by jstocky on 2008-10-18
When I use the Propriatary driver called "**nVidia accelerated graphics card (Latest cards)**" I am able to select "visual effects/extra", and it works...sort of, but the problem is that the video resolution is crappy and LARGE! I'm guessing 640x480.

The system works fine with the propriatary driver disabled.

Is there a way to fix this so my resolution is better and I can also use the desktop "visual effects/extra"?

Last night I was trying to load a older driver, and the system crashed. I reloaded Ubantu this morning.

2 days ago with the same system, I loaded SUSE and the graphics worked and a great resolution, but I didn't like the OS as well so I changed it to Ubantu again.

My system
AMD 3200
1 gig memory
nVidia 6800 graphics card
latest version of ubantu

Your help is greatly appreciated
Jim

---

### Post by eternalnewbee on 2008-10-18
> **jstocky said:**
> When I use the Propriatary driver called "**nVidia accelerated graphics card (Latest cards)**" I am able to select "visual effects/extra", and it works...sort of, but the problem is that the video resolution is crappy and LARGE! I'm guessing 640x480.

The system works fine with the propriatary driver disabled.

Is there a way to fix this so my resolution is better and I can also use the desktop "visual effects/extra"?

Last night I was trying to load a older driver, and the system crashed. I reloaded Ubantu this morning.

2 days ago with the same system, I loaded SUSE and the graphics worked and a great resolution, but I didn't like the OS as well so I changed it to Ubantu again.

My system
AMD 3200
1 gig memory
nVidia 6800 graphics card
latest version of ubantu

Your help is greatly appreciated
Jim

Have you tried in Main Menu > System > Preferences > Screen Resolution?

---

### Post by Victormd on 2008-10-18
Try using envy-ng to install your graphics driver. Open synaptic package manager and search for **envyng**. Once installed, it will be under applications>tools and you can run it from there. Then just choose NVIDIA, let envyng autoselect the best driver and that should do the trick.

---

### Post by jstocky on 2008-10-18
> **Victormd said:**
> Try using envy-ng to install your graphics driver. Open synaptic package manager and search for **envyng**. Once installed, it will be under applications>tools and you can run it from there. Then just choose NVIDIA, let envyng autoselect the best driver and that should do the trick.
I searched for enyng and found 3 different files (Core, GTK and qt) what do I pick? I think this is how I got it to crash last night. It wouldn't boot.

---

### Post by eternalnewbee on 2008-10-18
> **jstocky said:**
> I searched for enyng and found 3 different files (Core, GTK and qt) what do I pick? I think this is how I got it to crash last night. It wouldn't boot.

Depends on your Windows Manager. If you are using Gnome I'd say go for GTK.
QT is I think for KDE. As for Core, I think you'd have to compile yourself...

---

### Post by Victormd on 2008-10-19
> **jstocky said:**
> I searched for enyng and found 3 different files (Core, GTK and qt) what do I pick? I think this is how I got it to crash last night. It wouldn't boot.

If you're using Ubuntu or Xubuntu, then install envyng-gtk. Otherwise, use envyng-qt. Once you select the corresponding package, synaptic will automatically select envyng-core and any other dependency. You can find more information about it [here]("http://albertomilone.com/nvidia_scripts1.html").

Let me know how this works out.

---

