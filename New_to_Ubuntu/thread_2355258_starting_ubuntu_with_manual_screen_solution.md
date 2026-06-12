---
title: "starting ubuntu with manual screen solution"
date: 2017-03-10
forum: New to Ubuntu
---

### Post by evaristegalois on 2017-03-10
Here is an odd problem. I have a SONY television with VGA input. The TV is fairly new, but it has a bug. When you plug in your computer and boot it up, ubuntu starts off fine, but then the video completely disappears and I get a "no video input" message. I think I know why this happens. Ubuntu requests the screen resolution, and the SONY monitor gives it the wrong one! I also had this issue with a Windows computer and was able to solve it by manually going into the screen resolution dialog box to change it. 

Here is the problem: in Windows you can do this blindly. You basically go through the steps with another monitor and then count your tab keys and arrow keys to do it on the defective SONY TV. In Ubuntu, if you use the Screen Display settings, you need a mouse. A mouse is no good when you can't see anything.

So here is the question. How do you change the screen resolution manually? There is a program called xrandr that works from the terminal and it appears to do some useful things, but I haven't had any luck with it. Any suggestions?

---

### Post by DuckHook on 2017-03-12
Try booting with the nomodeset kernel setting. Please post your complete computer specs, most importantly the video card.

---

