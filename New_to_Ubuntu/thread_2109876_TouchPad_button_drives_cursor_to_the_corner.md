---
title: "TouchPad button drives cursor to the corner"
date: 2013-01-28
forum: New to Ubuntu
---

### Post by villamil on 2013-01-28
I am running Ubuntu 12.10 on a Lenovo IdeaPad P500.  I have an issue with the touch-pad which manifests in two different ways. Let me explain.

This laptop is one whose touch-pad buttons are an extension of the pad itself.  In order to click, I have to just press the lower end of the pad, as there is no actual button piece.  Usually I move the (mouse/touch-pad) cursor with my right hand, and click with my left hand.  The first manifestation of the issue is that half of the times that I click with my left hand, the computer drives the cursor to the lower left corner of the screen, where the first button is situated (where I clicked).

The second manifestation is the opposite.  Whenever I don't click, but I happen to touch the touch-pad with my left hand, the mouse cursor will get fixed in it's place, even if I am moving the cursor with my right hand.  

These two manifestations make me think that there is an issue on the configuration of the touch-pad on how it recognizes a second hand or finger; maybe it's not erratic, it's just not normal, and it has been like a pebble in my shoe; making me take conscience every time I am using the touch-pad. 

Thank you for your help in showing me how to fix this issue. 
Diego

---

### Post by tgalati4 on 2013-01-28
Perhaps your touchpad needs recalibration.  There might be a BIOS menu to do that or a program that you can run to set the offset and sensitivity values.  As far as the buttons are concerned, open a terminal and run:

```
xev
``` and put the mouse in the white box and push on the "mouse" buttons and see what response you get.  You will see both press and release responses that will look something like:

ButtonPress event, serial 35, synthetic NO, window 0x2c00001,
    root 0x131, subw 0x0, time 9641158, (114,120), root:(127,604),
    state 0x0, button 1, same_screen YES

ButtonRelease event, serial 35, synthetic NO, window 0x2c00001,
    root 0x131, subw 0x0, time 9641272, (114,120), root:(127,604),
    state 0x100, button 1, same_screen YES

ButtonPress event, serial 35, synthetic NO, window 0x2c00001,
    root 0x131, subw 0x0, time 9642294, (114,120), root:(127,604),
    state 0x0, button 3, same_screen YES

ButtonRelease event, serial 35, synthetic NO, window 0x2c00001,
    root 0x131, subw 0x0, time 9642418, (114,120), root:(127,604),
    state 0x400, button 3, same_screen YES

ButtonPress event, serial 35, synthetic NO, window 0x2c00001,
    root 0x131, subw 0x0, time 9643674, (114,120), root:(127,604),
    state 0x0, button 2, same_screen YES

ButtonRelease event, serial 35, synthetic NO, window 0x2c00001,
    root 0x131, subw 0x0, time 9643863, (114,120), root:(127,604),
    state 0x200, button 2, same_screen YES

For pressing the 3 mouse buttons.  If you are getting a bunch of spurious inputs, it could be you have some grit stuck on the edge of the touchpad or perhaps moisture.

---

### Post by ntzrmtthihu777 on 2013-01-28
Damn you are upset lol. may be a better idea to put stuff like that in code tags to prevent spurious smilies ;)

OP: Maybe you are accidentally touching two points at once causing the jump.

---

