---
title: "changing the resolution"
date: 2012-10-28
forum: New to Ubuntu
---

### Post by znjrols on 2012-10-28
I have this problem, and it's killing me. Would appreciate any help.

When I tried to install Ubuntu 12.04 on my laptop (Intel integrated graphics) I got a black screen. So I Googled it a little, and found that a solution is to add an option "nomodeset", so I installed it with "nomodeset" option and then changed the file "/etc/default/grub", so now my laptop always boots with "nomodeset". If I set it to boot without it, I just get black screen.

The problem is that in Display Settings I get only resolutions 800x600 and 1024x768, and not a desired one 1368x768. 
So I Googled that also, and used some comands, cvt 1368 768, xrandr newmode, xrandr addmode. Now I have 1368x768 resolution in Display Settings, but when I try to change to that resolution I get an error:

"THE SELECTED CONFIGURATION FOR DISPLAYS COULD NOT BE APPLIED
required virtual size does not fit available size: requested=(1368,768), minimum=(800,600), maximum=(1024,768)"

I tried also with typing just "xrandr" in terminal and I can see there a line "1368x768_60.00   59.9 ", and I tried with the comand "xrandr --output default --mode 1368x768_60.00" and I got an error:
"xrandr: Failed to get size of gamma for output default
xrandr: Configure crtc 0 failed"

Someone got any thoughts ? :)

update: The keybord shortcut screen doesn't appear when I hold the super key for 2 seconds, and I've read that thats because I've started the session in 2D mode. Maybe thats related to this problem ?

---

### Post by mikewhatever on 2012-10-28
Can you post the computer specs, including the graphics. If it's a desktop, post also the monitor specs and the way the two are connected.
Unity2d doesn't require 3d, which makes it a good option for older hardware, but it shouldn't have anything to do with resolution changing.

---

### Post by znjrols on 2012-10-28
Memory : 1.9GB
Processor: Celeron(R) Dual-Core CPU T3000 @ 1.80GHz × 2
Graphics: VESA: Intel(r)Cantiga Graphics
OS type 32-bit

It's a laptop.
Thanks for a reply

---

### Post by mikewhatever on 2012-10-28
Do you have 'default' specified as possible output by xrandr? Usually on a laptop, you'd have something like LVDS1.

---

### Post by znjrols on 2012-10-28
I just want to add one more imortant thing

I've set ubuntu to boot without the option "nomodeset" and of course I got black screen. But when I point the flashlight to the screen I can see what's on the screen. So, the screen is not blank, it's just missing the backlight. And the most important thing is that when it boots up like that, the resolution is set as it should be, 1368x768. So if I could just do something to prevent getting black screen while booting without nomodeset..

---

### Post by znjrols on 2012-10-28
rols@uhu:~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 800 x 600, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768       61.0* 
   800x600        61.0



I believe it's a problem with nomodeset, because of that drivers don't recognize my laptop's monitor, or graphic card, I wouldn't know.

---

### Post by mikewhatever on 2012-10-29
Have you tried increasing the display brightness?

---

### Post by znjrols on 2012-10-29
yes, nothing happens..

---

### Post by znjrols on 2012-10-29
Oh god... finally.... this helped

[http://ubuntuforums.org/showthread.php?t=1900024](http://ubuntuforums.org/showthread.php?t=1900024)

I booted without "nomodeset" option, and I adjusted my backlight down then up, just before ubuntu starts....

Thanks for your time anyway. I guess I didn't searched enough for solution for this problem before I posted

---

