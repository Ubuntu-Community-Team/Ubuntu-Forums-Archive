---
title: "How to make SLI run smooth with Compiz"
date: 2006-09-06
forum: Outdated Tutorials &amp; Tips
---

### Post by BoudahXL on 2006-09-06
First off, this is my first post here, so take it easy on me :D 

Anyway, I have been installing and re-installing Ubuntu 6.06.1 couple times over the last week with compiz trying to make everything work the way I wanted it to.

But each and every single time I turned on SLI frame rates were way down in compiz interface unresponsive...I also had some graphic anomalies in certain apps (blank menus, grey bars insetad of text inside OpenGL apps windows, Google Earth is an example)

Been googling a lot reading Nvidia websites, devs site, notes, trial and errors...Here is what I found.You can make SLI run as smooth as single card setup under Compiz.

Pro:

-Faster OpenGL frame rates under heavy cpu load.
-Faster OpenGL when 2 or more 3D apps window are active.
-Warm feeling of running your second card.

Con:

-Not a single frame faster for single application.

Howto:
My settings
-Compiz 0.0.13.45
-cgwd 0.68-0
-Compiz-plugins 0.16-0
-Xgl 7.0.0
-nvidia-glx 1.0.8762
-csm 0.5-0 <--Which replace gnome-compiz-manager

My Xorg setup (declare only one device even though you have two cards, unless you attache two displays"

Section "Device"
    Identifier     "NVIDIA Corporation NV43 [GeForce 6600 GT]"
    Driver         "nvidia"
    Option         "RendelAccel"           "true"
    Option         "AllowGLXWithComposite" "true" 
    Option         "Triplebuffer"          "true"
    Option         "NoFlip"                "True"
    Option         "SLI"                   "SFR"
    Option         "ConnectedMonitor"      "CRT"
EndSection

AllowGLXWithComposite most compiz howto's says to turn it on, could someone explain why, it contradict nvidia's instructions.

NoFlip this option is "supposed" to be on for xgl+compiz according to devs at nvidia (quoted from SUSE's website)

SLI options are "false","true","auto","AFR","SFR" 
-"false" is one GPU render, fastest* default setting so far for me
-"true" and "auto" produce the same result, sluggish performance
-"AFR" or Alternate frame rendering, is a lot better than "true" or "auto" but it's about 20% slower in general except under heavy load or with multiple OpenGL windows opened, then it's faster than "false"
-"SFR" split frame rendering, as fast as "false" worst case scenario -5%, but as soon as your cpu crunch you'll be ahead with this setting, same as "AFR" it is better with multiple OpenGL window opened.
-"ConnectedMonitor" I have a KVM so this is only a precaution on my part you can ignore that line

DO NOT COPY THE IDENTIFIER LINE, use your own videocard string.

Note: When I say multiple OpenGL window opened I mean windowed OpenGL applications, even an OpenGL clock or small widget make a difference.

My 2 cents, that's 2x1 cents in SLI mode.

---

### Post by sigmaris on 2006-09-07
> **BoudahXL said:**
> 
Section "Device"
    Identifier     "NVIDIA Corporation NV43 [GeForce 6600 GT]"
    Driver         "nvidia"
    Option         "RendelAccel"           "true"
    Option         "AllowGLXWithComposite" "true" 
    Option         "Triplebuffer"          "true"
    Option         "NoFlip"                "True"
    Option         "SLI"                   "SFR"
    Option         "ConnectedMonitor"      "CRT"
EndSection

AllowGLXWithComposite most compiz howto's says to turn it on, could someone explain why, it contradict nvidia's instructions.


The reason why most compiz howtos say to turn AllowGLXWithComposite on is that people who don't know enough about how XGL and Compiz work see "GL" and "Composite" and think "Oh that must be good". This setting turns on OpenGL when you are using the Composite extension on the plain old Xorg server (NOT XGL). 

Neither this setting, nor the Composite extension on the Xorg server, nor "RenderAccell" on the Xorg server, are needed when using XGL. All it requires, on the X server that is "hosting" it, is the ability to use plain old OpenGL (preferably hardware accelerated). XGL provides its own Composite extension, XRender acceleration and draws and composites everything using OpenGL, in its own fullscreen window.

---

### Post by BoudahXL on 2006-09-07
Thanks you the quick reply :)

---

