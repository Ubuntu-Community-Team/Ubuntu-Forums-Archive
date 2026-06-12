---
title: "Dual Monitor Frustration!!!"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by davidwfox on 2008-08-09
I would appreciate some guidance to resolve my inability to get an external monitor to work properly.

I have an ATI Radeon IGP 330M/340M/350M graphics card in a Sony PCG-K74 laptop, and I have an Acer 17" AL1716 external monitor. I've just installed Ubuntu 8.04 and now the external monitor, that worked fine with version 6.?? (whatever that number was), will not function properly.

When I first switch on and the dual boot menu appears, both monitors display correctly. However, by the time we get to the Ubuntu log-in screen the external monitor has gone blank. If I go into System/Preferences/Resolution, both monitors are shown - Laptop, and Acer 17" - so the system is obviously aware of the external monitor.

What do I do to make the external monitor show a display? I've browsed numerous threads but can find nothing that tells me, in simple terms, what to do. Any guidance will be much appreciated, before I throw the monitor through the nearest window!!!

In reply, please keep in mind that I'm still a virtual Linux novice, so I'll need very specific descriptions on what to do.

---

### Post by starcannon on 2008-08-09
My Laptop dual-monitor frustration was solved by a work around I discovered while trial and erroring the problem. My solution is not ideal, but will work until a better solution presents itself.

At the Boot or Grub Menu(stop booting by pressing escape at grub) use your FN+external-monitor-key cycle through until you see the grub or boot menu(if you pressed pause) screen on the Laptop, External, or Both Monitors, depending on what your trying to accomplish, then allow boot to continue. 

Thats the best I can come up with, if your trying to do a dual head monitor setup, then I don't know.

---

### Post by davidwfox on 2008-08-09
That's part of the frustration. The GRUB menu *does* appear on both screens. It's once I select the boot item, and the Ubuntu log-in screen loads, that the external monitor goes blank!

---

### Post by Norman Grahams on 2008-08-09
I've just recently been playing with making a monitor work, and have I think the same situation as you.

[this]("http://ubuntuforums.org/showthread.php?t=861643") thread pointed me to the solution, which is using xrandr. Instructions are at [http://www.thinkwiki.org/wiki/Xorg_RandR_1.2]("http://www.thinkwiki.org/wiki/Xorg_RandR_1.2").

My xorg.conf looked a little different to what's there, so I didn't change it at all. To use my external monitor rather than my laptop screen, I use the command:

xrandr --output LVDS --off --output VGA --auto

To switch back, I change LVDS to auto and VGA to off. They can both be on, but for that it seems you want to add a switch to say where the VGA goes, in the simplest case --same-as LVDS, so:

xrandr --output LVDS --off --output VGA --auto --same-as LVDS

use xrandr -q to check what names it uses for your devices.


To get the two screens side by side, you can use eg. --right-of LVDS or --below LVDS, but this may make the total size bigger than your virtual screen size (see xrandr wiki). My virtual screen size was set to max 1280x1280, and I haven't yet been able to change that.



If any of this isn't clear, or doesn't work, do say.

---

### Post by davidwfox on 2008-08-09
That half worked.

xrandr --output LVDS --off --output VGA --auto 
turned off the laptop screen OK but still left the other one blank, so then I had two blank screens! Not quite what I wanted.

xrandr -q shows:
Screen 0: minimum 320 x 200, current 1280 x 1200, maximum 1280 x 1200
VGA-0 connected 1280x1024+0+0 (normal left inverted right x axis y axis) 338mm x 270mm
   1280x1024      60.0*+   75.0     59.9  
   1152x864       74.8  
   1024x768       75.1     70.1     60.0  
   832x624        74.8  
   800x600        72.2     75.0     60.3     56.2  
   640x480        75.0     72.8     60.0  
   720x400        70.1  
DVI-0 disconnected (normal left inverted right x axis y axis)
LVDS connected 1024x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768       60.0*+   60.0  
   800x600        60.3  
   640x480        59.9  
S-video disconnected (normal left inverted right x axis y axis)

The resolution shown for VGA-0 is the same as I see when I run System/Preferences/Resolution as noted in my first post.

So then I tried: xrandr --output LVDS --auto --output VGA-0 --auto
That at least left the laptop screen operating, but it still didn't help the external screen.

Any thoughts on what to try next?

---

### Post by Norman Grahams on 2008-08-10
Did you boot with the external screen plugged in?
I find that if I boot without it plugged in, xrandr -q says it's there, but somehow the signal never gets to the screen.
If I boot with it in, the external screen works but brightness control on my laptop screen stops working.

---

### Post by davidwfox on 2008-08-11
Yes, the external screen is always plugged in.
What makes the frustration worse is that the b--- thing works fine with Win XP. The laptop displays corrrectly, and the Acer 1716 displays correctly - as they both did with Ubuntu 6.?? a year or more back!

---

### Post by Norman Grahams on 2008-08-11
Try sudo displayconfig-gtk

---

