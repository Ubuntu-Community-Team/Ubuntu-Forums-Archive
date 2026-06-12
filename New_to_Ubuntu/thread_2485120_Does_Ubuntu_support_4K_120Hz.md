---
title: "Does Ubuntu support 4K 120Hz?"
date: 2023-03-20
forum: New to Ubuntu
---

### Post by gregory-andrik on 2023-03-20
Hello everyone,

I am new to Ubuntu and I am thinking about buying an ultrawide monitor to use for coding. I am accustomed to Windows 11 smooth refresh rate though, and I will have a hard time going back to 60Hz. 

I tried to find a direct answer to my question and to my surprise, it was difficult.

---

### Post by cainesaj on 2023-03-20
Boot from the live ISO of your preferred Ubuntu desktop flavour and take a look at the settings for video. In GNOME it's *Displays*, where you will find options for all detected settings *Resolution* and *Scale*. Typically these will all have optimal stable defaults.

The difficulty you encountered is that the relationship between Ubuntu - a Linux distribution with many variants and multiple releases - and specific video capabilities depends of so many factors and the useful "it depends" answer is likely too much to try to address them all (each relevant hardware, interface - HDMI/DP/USB, cable, firmware, OS flavour, release, driver, display system - Wayland/Xorg, settings, etc.). The other reason is that generally this kind of thing just works&#8482; in the vast majority of cases, hence almost all discussion concerns the few cases in which some specific combination does not (fully) work at some point.
Unless you have some extremely new or unusual hardware, then it will likely work exactly as you want with no effort needed on your part.

---

### Post by gregory-andrik on 2023-03-20
As a matter of fact, I booted from a USB stick and the moment i changed the refresh rate I lost half of display and it was a pain to reset it to 60Hz. I don't know why this happened, but it was the first thing I did once Ubuntu loaded up.

---

### Post by MAFoElffen on 2023-03-21
It is not as simple as that, and yet you are making it much more difficult that it really is.

What that means is that a GPU, the video graphics processing unit... GPU, and it's corresponding graphics driver is capable of various resolutions, refresh rates, and "modes". 

A display also has it's designed resolutions, refresh rates, and modes.

The system tries to figure out a balance between the two. A mode that the video GPU can transmit, a matching mode the display can render. Usually there are choices.

You want to see some of that with what you have now? At the Graphical Login, ensure that the Desktop you boot from there is Xorg (Not wayland)...

Open a terminal:
```

mafoelffen@Mikes-ThinkPad-T520:~$ xrandr -q
Screen 0: minimum 8 x 8, current 1920 x 1080, maximum 16384 x 16384
LVDS-0 disconnected (normal left inverted right x axis y axis)
DP-0 disconnected (normal left inverted right x axis y axis)
DP-1 disconnected (normal left inverted right x axis y axis)
DP-2 disconnected (normal left inverted right x axis y axis)
DP-3 disconnected (normal left inverted right x axis y axis)
DP-4 disconnected (normal left inverted right x axis y axis)
DP-5 disconnected (normal left inverted right x axis y axis)
LVDS-1-1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 344mm x 193mm
   1920x1080     60.00*+  60.00    50.00  
   1680x1050     60.00  
   1400x1050     60.00  
   1600x900      60.00  
   1280x1024     60.00  
   1400x900      60.00  
   1280x960      60.00  
   1440x810      60.00  
   1368x768      60.00  
   1280x800      60.00  
   1280x720      60.00  
   1024x768      60.00  
   960x720       60.00  
   928x696       60.00  
   896x672       60.00  
   1024x576      60.00  
   960x600       60.00  
   960x540       60.00  
   800x600       60.00  
   840x525       60.00  
   864x486       60.00  
   700x525       60.00  
   800x450       60.00  
   640x512       60.00  
   700x450       60.00  
   640x480       60.00  
   720x405       60.00  
   684x384       60.00  
   640x360       60.00  
   512x384       60.00  
   512x288       60.00  
   480x270       60.00  
   400x300       60.00  
   432x243       60.00  
   320x240       60.00  
   360x202       60.00  
   320x180       60.00  
VGA-1-1 disconnected (normal left inverted right x axis y axis)

```
Those are the resolutions x refresh rate = modes on my laptop, using it's display. It I set a mode that is outside the capabilities of the connected display, yes it will be not good.

Note that the graphics GPU in my laptop can display a higher resolution and different refresh rates. Thosee would show differently with the above command, if I was connected to an external Display of better quality.

---

