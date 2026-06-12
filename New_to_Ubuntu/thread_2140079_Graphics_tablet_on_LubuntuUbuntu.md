---
title: "Graphics tablet on Lubuntu/Ubuntu"
date: 2013-04-28
forum: New to Ubuntu
---

### Post by seal308 on 2013-04-28
I am using a wacom bamboo tablet with both my Mac and lubuntu computer.
On my Mac it works the way I want it to.
No matter where the cursor is on screen, wherever I put my pen on the graphics tablet it stays in the same place. 
Therefore the position of the cursor is independent of where the pen is on my graphics tablet after the pen has been lifted of the tablet. 
Also the sensitivity is low. When I say sensitivity it mean it usually takes multiple strokes of the pen to get from one side of the screen to another.
However on my lubuntu computer it is exactly the opposite.
It appears as though that wherever  y pen is on my graphics tablet influences where the cursor is on the screen.
That is, if my pen is on the top right of the graphics tablet the cursor will be on the top right of the screen and so on.
Is there a way to make my graphics tablet work the same way it does on my mac?

Thanks

---

### Post by Favux on 2013-04-28
Hi seal308,

Driver default is Absolute Mode.  Relative Mode like on your Mac is for a mouse or touchpad.  See the Wacom settings applet in System Settings.   But if you want to change Modes find the pen's "device name" using the following command in a terminal:
```
xinput list
```
Then use the Mode parameter with an xsetwacom set command:
```
xsetwacom set "device name" Mode Realtive
```
More information available here:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:HOWTO](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:HOWTO)

---

### Post by seal308 on 2013-06-12
I figured out my problems.

Problem 1: Coordinates of graphics tablet exactly matches the coordinates of the screen.
Solution: Follow Favux's instructions.

Problem 2: The cursor seems to be moving too fast.
Solution:
Need to de accelerate the input device (The wacom device stylus)

First find the Constant Deceleration
```
xinput list-props "device name"
```

Looking down the list you should see "Device Accel Constant Deceleration (256):	1.000000" as a default

I wanted half the speed I was getting so I put 2 as the constant deceleration by:

```
xinput set-prop "device name" --type=float "Device Accel Constant Deceleration" 2.000000
```

This worked perfectly.
I hope others will find this useful.

---

