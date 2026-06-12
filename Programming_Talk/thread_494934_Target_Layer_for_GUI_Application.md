---
title: "Target Layer for GUI Application"
date: 2007-07-07
forum: Programming Talk
---

### Post by lightnb on 2007-07-07
I would like to write a GUI application for Linux and am looking for some input and guidance. The purpose of the program is very industry specific (think: applied robotics), and it will be a dedicated machine running it. In other worlds, when the computer boots, the program is launched automatically, and the user won't have a need to run any other program(s).

Given this, do I need to use a desktop environment? I'm not sure which elements (hardware control, window management, etc.) run on which layers (The Kernel, the X server, the desktop environment, etc.).

Should my target (OS?/Layer?) be a stripped down version of KDE, or should .... I don't know- there's too many thing I'm uncertain of to be able to ask the right question(s).

Here's what I do know:

**Hardware:**
Needs support for multiple monitors, some of which will be touch screens.
Support for standard USB Keyboard and Mouse
It will have custom input devices (example: wheels, sliders, buttons)
It will have custom output devices (USB)


**Software:**
Multiple users, each with their own 'profile' of settings (don't know if this can/should be based on/use the existing linux login system?)

I'm hoping that someone can point me in the right direction so that I know which 'layer' I should be studying.

Thank you in advance, it's appreciated!

---

### Post by AlexThomson_NZ on 2007-07-07
I would use a desktop environment (I would use Gnome personally), that way things like USB keyboards, mice, touchscreens are abstracted, and programming graphical widgets is fairly easy once you know.

Your different input devices (I assume you are talking about physical buttons, sliders, etc.), will probably need a driver to be written- probably not that hard if you know the signals it's sending, which will access the kernel.  You program in turn will access the driver.

With regards to multiple users, it's hard to say how to implement it with the information supplied.  Also, how low spec is this machine (ie. it is capable of running a gnome install right?)  it is possible to have a very lightweight graphical desktop, but you might find it a bit harder to find good programming docs, so steer clear if you can and keep it simple...

So target environment (IMHO)
 * basic gnome desktop
 * Your custom driver for physical inferace installed
 * Your Gnome app installed

HTH

---

### Post by lightnb on 2007-07-13
Thanks Alex,

I guess it makes sense not to re-invent the wheel so to speak by programming USB drivers, when they already exist.

In Gnome, is it possible to remove menu bars and other things that make it look like a personal computer? Also can the programs' windows be 'locked' full screen on each screen so that they don't/can't 'slide around' and don't have menu bars?

Which language would you recommend? c++? I've been using Kdevelop for a while now, but can it create gnome apps too? or is there a 'Gdevelop' or something?

There are no hardware limitations- I can make it as fast of a machine as it needs to be.

Thanks again,

Nick

---

### Post by ankursethi on 2007-07-13
You can do anything you want to GNOME. You can add/remove menubars/toolbars etc. from the desktop, and you can do the same in your application as well. I don't know how to prevent them from being dragged around the place, but I guess if you make your application "fullscreen" and remove the window decorations etc. you might be able to achieve this effect.

Alternatively, you can try using a different window manager with GNOME which can allow more control over your windows.

---

### Post by AlexThomson_NZ on 2007-07-13
> **lightnb said:**
> Thanks Alex,

In Gnome, is it possible to remove menu bars and other things that make it look like a personal computer? Also can the programs' windows be 'locked' full screen on each screen so that they don't/can't 'slide around' and don't have menu bars?

Which language would you recommend? c++? I've been using Kdevelop for a while now, but can it create gnome apps too? or is there a 'Gdevelop' or something?

Nick

As the previous poster mentioned, you can do that stuff easily with gnome or KDE (as you probably well know).  If you're experienced with KDE, why not just use that though?  I think KDevelop is probably better than anything that exists currently on Gnome (Glade+Anjuta/Geany)

At the risk of p!ssing off the python fanclub here, I would say still with C++ and C for the driver if required (unless your USB interface is already part of the existing stack- I'm not too familiar with how USB drivers are implemented on Linux)

---

