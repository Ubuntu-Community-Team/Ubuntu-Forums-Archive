---
title: "Problem loading Blender"
date: 2012-01-10
forum: New to Ubuntu
---

### Post by Futant on 2012-01-10
Hello, firstly, I'm new to all this so please go easy! I've just installed Ubuntu 11.10 (dual boot with Windows 7,) on a new Dell XPS L502x (Intel Core i5-2410M, 500GB HDD partitioned, 100MB for Ubuntu), 4GB RAM, NVIDIA GeForce GT 525M 1GB DDR3, not sure what's relevant to the problem?). Everything seems to work fine (although icons from system settings keep disappearing, anyone?), I downloaded Gimp with no problem and have just downloaded Blender 2.58, which appears in the launcher but won't start. The only thing that happens when I click on it is that the icon flashes. When I try launching from the terminal I get this - 



Info: Config directory with "startup.blend" file not found.
Xlib:  extension "GLX" missing on display ":0".
/build/buildd/blender-2.58-svn37702/intern/ghost/intern/GHOST_WindowX11.cpp:194: X11 glXQueryVersion() failed, verify working openGL system!
initial window could not find the GLX extension, exit!


I have also downloaded it from the Blender site, it still won't launch. I have found similar questions on here but they are old, and nothing so far has helped. Is it that I don't have enough memory allocated for Ubuntu?

Any ideas and help would be much appreciated!

---

### Post by mcduck on 2012-01-10
Do you have nVidia's drivers installed for your graphics card? And does your computer use Optimus to switch between integrated GPU and the nVidia one?

The error about missing GLX is telling you that the system isn't able to handle OpenGL graphics...

---

### Post by Futant on 2012-01-10
> **mcduck said:**
> Do you have nVidia's drivers installed for your graphics card? And does your computer use Optimus to switch between integrated GPU and the nVidia one?

The error about missing GLX is telling you that the system isn't able to handle OpenGL graphics...

Thanks for replying, the drivers are installed, and the computer does indeed have Optimus... I have read about Ironhide, but am not sure if I am on the right track... Should I just try to turn the nvidia card off?

---

### Post by mcduck on 2012-01-10
> **Futant said:**
> Thanks for replying, the drivers are installed, and the computer does indeed have Optimus... I have read about Ironhide, but am not sure if I am on the right track... Should I just try to turn the nvidia card off?

I'd suggest the opposite, tunring the integrated GPU off if you happen to have that option in BIOS or something. Of ocurse which one you want to use is a choce of performance versus battery life, but Blender would definitely benefit from the better GPU.

Ironhide might do the trick, it seems. I have no persoanl experience about it (HP has permanently disabled the Intel's integrated GPU on my laptop because of all the problems Optimus still has, so I don't even have the option to switch between the two GPUs)

---

### Post by Futant on 2012-01-10
Thanks for your help, though I think for the moment I'll use Windows for Blender...

---

