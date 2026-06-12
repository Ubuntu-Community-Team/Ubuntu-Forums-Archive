---
title: "Visual Effects"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by 124C41+ on 2008-04-28
I am trying yo install/run Compiz for the visual effects. 

I installed the EnvyNG drivers for my card with out a problem. (after lots of playing around) and also checked to see if my card was VGA compatible in the terminal. Which it is. Now I am looking to getting these visual effects working. I don't know if 3d acceleration is working nor do i know how to test for this. 

I understand that compiz for the most part installed on on 8.04. When I try to enable the visual effects in System>Preferences>Appearance from basic to extra it goes to a white screen. 

I have tried enabling restricted drivers but when I go to the driver window there are no devices I can select to install restricted drivers for.

What is my next step to getting Compiz working on my machine.

---

### Post by 124C41+ on 2008-04-28
bumpo

---

### Post by oedha on 2008-04-28
here's what i did to my ATI RV505
1. open terminal then type : **sudo apt-get install xorg-driver-fglrx**
2. after that **sudo apt-get install xserver-xgl**
3. **sudo apt-get install compizconfig-settings-manager**
4. go to system - administration - hardware drivers ( make the ATI enable )
5. reboot
6. go to system - preferences - advanced Desktop effects setting
7. set the compiz effects

or maybe you can install ATI driver from [http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)

---

### Post by 124C41+ on 2008-04-29
Alright I have Compiz working but now my Cube is not unfolding properly. Instead of a cube its just clones of the same desktop all set beside each other. How do I get the cube to unfold as an actual cube instead of a line of desktops?

And if you need a screenshot I cant figure out how to take those either. :confused::(

---

### Post by Golem XIV on 2008-04-29
> **124C41+ said:**
> Alright I have Compiz working but now my Cube is not unfolding properly. Instead of a cube its just clones of the same desktop all set beside each other. How do I get the cube to unfold as an actual cube instead of a line of desktops?

And if you need a screenshot I cant figure out how to take those either. :confused::(

Go to System -> Preferences -> Advanced Desktop Effects Settings.
Disable Desktop Wall
Enable Desktop Cube
Enable Rotate Cube
If you want, you can also play around with Cube Caps, 3D Windows, etc.

To take a screenshot, Applications -> Accessories -> Take Screenshot

---

### Post by 124C41+ on 2008-04-29
Thats what i already have. Walls disabled. Rotating Cube works cause I can switch between desktops but I want to be able to zoom out and look at the cube. Halp!

---

### Post by Golem XIV on 2008-04-29
> **124C41+ said:**
> Thats what i already have. Walls disabled. Rotating Cube works cause I can switch between desktops but I want to be able to zoom out and look at the cube. Halp!

Ctrl-Alt-left or right arrow will rotate one desktop at a time (same as clicking the workspace selector on the panel).
Ctrl-Alt-down arrow will unfold the cube into a strip (which seems to be what you're getting now).

But apparently what you want is Ctrl-Alt-click-and-drag.  Give it a try.

---

### Post by 124C41+ on 2008-04-29
That did it! Thank you so much! You get a thanks!

---

