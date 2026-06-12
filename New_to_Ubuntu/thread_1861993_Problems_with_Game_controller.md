---
title: "Problems with Game controller"
date: 2011-10-16
forum: New to Ubuntu
---

### Post by mschooler93 on 2011-10-16
I just bought a Game controller, and it doesn't play in a lot of things. I can make it work in Gens/gs, but nothing else. Once I restarted, (thinking it would help) it then for some reason, took over as the mouse. Whenever I try to calibrate it, I can't because it moves the mouse somewhere else. I was trying to get it to work all last night, so I am a bit foggy about all what I installed, but I have right now, joystick, and xserver-xorg-input-joystick. I also installed all the things to make jscalibrator work, because I read somewhere else that it would work. So, that's not installed, but it's dependencies are still I think. And, I had joy2key, and another one but they are off right now.

So, when I use it in anything, it just works as a mouse (which wouldn't be so bad, if it wasn't so fast) When I try to use jscalibrator, it doesn't show the whole window, so it cuts off a lot of the text. When I calibrate, it doesn't do much of anything, and when I switched to logical view, the one axis (axis 2) was going crazy, the numbers were always going up and down. What's strange, is that axis 2 is like an extra one. It is the left-right on the left analog stick (link to the controller I bought at the bottom, but basically it's like a playstation 2 controller) is on another one, too. And, the other one works OK. 

I tried to use the terminal to disable this axis (2) and see if that fixed it, but I don't understand the commands. I did jscal -p /dev/input/js0 and thought that it would be easy, just change the axis to somewhere else, or just remove it, but it gave back really big numbers ```
jscal -s 7,1,0,112,142,5534751,5534751,1,0,112,142,5534751,5534751,1,0,112,142,5534751,5534751,1,0,112,142,5534751,5534751,1,0,112,142,5534751,5534751,1,0,0,0,536870912,536870912,1,0,0,0,536870912,536870912 /dev/input/js0
``` and I can't copy-paste in the terminal, without it entering it before I get a chance to type anything else. Even in the test, the highest the number got was 32767, so I don't know if this is something wrong with the controller, or what. 

So, I would appreciate it if someone could help me get this working, or tell me what to do to fix it. 
I have ubuntu 10.04.

[http://www.radioshack.com/product/index.jsp?productId=3964949&filterName=Category](http://www.radioshack.com/product/index.jsp?productId=3964949&filterName=Category)

And, here is what it says about the controller at the top of the jstest screen. 

```
Driver version is 2.1.0.
Joystick (DragonRise Inc.   Generic   USB  Joystick  ) 
has 7 axes (X, Y, Z, Rx, Rz, Hat0X, Hat0Y)
and 12 buttons (Trigger, ThumbBtn, ThumbBtn2, TopBtn, TopBtn2, PinkieBtn, BaseBtn, BaseBtn2, BaseBtn3, BaseBtn4, BaseBtn5, BaseBtn6).
```

---

### Post by mschooler93 on 2011-10-16
Here is what it says for each button, and axis when I use jstest.

1 Button: (where the square would be on playstation)
```
Axes:  0:     0  1:     0  2:     0  3:-32767  4:-32767  5:     0  6:     0 Buttons:  0:on   1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10:off 11:of
```

2 Button: (where X would be on PS)
```
Axes:  0:     0  1:     0  2:     0  3:-32767  4:-32767  5:     0  6:     0 Buttons:  0:off  1:on   2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10:off 11:off
``` (it also clicks, primary click)

3 Button: (where circle button is on PS)
```
Axes:  0:     0  1:     0  2:     0  3:-32767  4:-32767  5:     0  6:     0 Buttons:  0:off  1:off  2:on   3:off  4:off  5:off  6:off  7:off  8:off  9:off 10:off 11:of
```  (this also clicks, secondary click)

4 Button: (where triangl is on PS)
```
Axes:  0:     0  1:     0  2:     0  3:-32767  4:-32767  5:     0  6:     0 Buttons:  0:off  1:off  2:off  3:on   4:off  5:off  6:off  7:off  8:off  9:off 10:off 11:of
```

5 Button: (where L1 is on PS)
```
Axes:  0:     0  1:     0  2:     0  3:-32767  4:-32767  5:     0  6:     0 Buttons:  0:off  1:off  2:off  3:off  4:on   5:off  6:off  7:off  8:off  9:off 10:off 11:of
```

6 Button: (where R1 is on PS)
```
Axes:  0:     0  1:     0  2:     0  3:-32767  4:-32767  5:     0  6:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:on   6:off  7:off  8:off  9:off 10:off 11:of
```

7 Button: (where L2 is on PS)
```
Axes:  0:     0  1:     0  2:     0  3:-32767  4:-32767  5:     0  6:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:on   7:off  8:off  9:off 10:off 11:of
```

8 Button: (where R2 is on PS)
```
Axes:  0:     0  1:     0  2:     0  3:-32767  4:-32767  5:     0  6:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:on   8:off  9:off 10:off 11:of
```

9 Button: (where select is on PS)
```
Axes:  0:     0  1:     0  2:  4729  3:-32767  4:-32767  5:     0  6:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10:off 11:of
Axes:  0:     0  1:     0  2:  4729  3:-32767  4:-32767  5:     0  6:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:on   9:off 10:off 11:of
Axes:  0:     0  1:     0  2:  1689  3:-32767  4:-32767  5:     0  6:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:on   9:off 10:off 11:of
Axes:  0:     0  1:     0  2:   675  3:-32767  4:-32767  5:     0  6:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:on   9:off 10:off 11:of
Axes:  0:     0  1:     0  2:     0  3:-32767  4:-32767  5:     0  6:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:on   9:off 10:off 11:o
```f

10 Button: (where start is on PS)
```
Axes:  0:     0  1:     0  2:     0  3:-32767  4:-32767  5:     0  6:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:on  10:off 11:of
Axes:  0:     0  1:     0  2:  1351  3:-32767  4:-32767  5:     0  6:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:on  10:off 11:of
Axes:  0:     0  1:     0  2:     0  3:-32767  4:-32767  5:     0  6:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:on  10:off 11:of
Axes:  0:     0  1:     0  2:     0  3:-32767  4:-32767  5:     0  6:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10:off 11:of
Axes:  0:     0  1:     0  2:   337  3:-32767  4:-32767  5:     0  6:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10:off 11:of
Axes:  0:     0  1:     0  2:     0  3:-32767  4:-32767  5:     0  6:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10:off 11:of
```


The joysticks are on digital mode, not analog mode when I test this. 

D-PAD UP:
```
Axes:  0:     0  1:     0  2:     0  3:-32767  4:-32767  5:     0  6:-32767 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10:off 11:of
Axes:  0:     0  1:     0  2:     0  3:-32767  4:-32767  5:     0  6:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10:off 11:of
```

D-PAD DOWN
```
Axes:  0:     0  1:     0  2:     0  3:-32767  4:-32767  5:     0  6: 32767 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10:off 11:of
```

D-PAD Left
```
Axes:  0:     0  1:     0  2:     0  3:-32767  4:-32767  5:-32767  6:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10:off 11:of
```

D-PAD Right
```
Axes:  0:     0  1:     0  2:     0  3:-32767  4:-32767  5: 32767  6:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off 10:off 11:of
```



I didn't post the two joysticks' output, because they are too long. If anybody needs them, tell me though and I will.
But, from what I can tell, the axes are these:

0 Axis: left stick, x-axis (also, D-PAD x-axis when in analog mode)
1 axis: left analog stick y-axis (again, D-PAD when in analog mode)
2 axis: left analog stick, x-axis (doesn't do anything in analog)
3 axis: right analog stick, x-axis (hard to do, because it scrolls up the terminal)
4 axis: right analog stick, y-axis
axis 5: D-PAD, x-axis (this goes from -1 to 1, where the other ones go to about 255, or 32767.)
axis 6: D-PAD, y-axis



```
Joystick has 7 axes and 12 buttons.
Correction for axis 0 is broken line, precision is 0.
Coeficients are: 112, 142, 5534751, 5534751
Correction for axis 1 is broken line, precision is 0.
Coeficients are: 112, 142, 5534751, 5534751
Correction for axis 2 is broken line, precision is 0.
Coeficients are: 112, 142, 5534751, 5534751
Correction for axis 3 is broken line, precision is 0.
Coeficients are: 112, 142, 5534751, 5534751
Correction for axis 4 is broken line, precision is 0.
Coeficients are: 112, 142, 5534751, 5534751
Correction for axis 5 is broken line, precision is 0.
Coeficients are: 0, 0, 536870912, 536870912
Correction for axis 6 is broken line, precision is 0.
Coeficients are: 0, 0, 536870912, 536870912

Calibrating precision: wait and don't touch the joystick.
Done. Precision is:                                               129,  129 Axis 4:  132,  132 Axis 5:    0,    0 Axis 6:    0,    0 
Axis: 0:     0
Axis: 1:     0
Axis: 2:     4
Axis: 3:     0
Axis: 4:     0
Axis: 5:     0
Axis: 6:     0
```
That is what it says, for the jcal calibrate.
I thought I'd put it in, because it says even when nothing is moving, that Axis 2 is 4, where everything else is 0.

---

### Post by mschooler93 on 2011-10-16
I should also say, that I know almost nothing about joysticks or gamepads. Before this, all I had was a gamecube for games. Should I just take the controller back, and wait until I get a Windows 7 to get a gamepad again? 

I actually bought it to play Portal (the first one), which I had bought before from steam, and I was gonna use steam on this computer, so I installed it (through wine) and then went out and bought the game controller, but then I got back and steam didn't work (was way too slow) and then the game controller went all f***ed up, and I have no idea what to do now.

---

