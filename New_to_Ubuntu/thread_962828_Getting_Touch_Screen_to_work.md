---
title: "Getting Touch Screen to work"
date: 2008-10-29
forum: New to Ubuntu
---

### Post by bitphire on 2008-10-29
Hello all!

My touch screen works it's just not even close to be accurate when the screen is touched. I have no idea on what to change or do as there isn't much documentation that I can find. Here is some info (xorg, etc...) If you need more let me know what and how to get it (what command to run).

[http://pastebin.com/m4070a45f](http://pastebin.com/m4070a45f)

Here is the man for elographics:
[http://linux.die.net/man/4/elographics](http://linux.die.net/man/4/elographics)

I spent 8 hours trying to figure this out with little to no success. The default xorg.conf worked the same as this elographics is.

Monitor is a: Dell E157FPT
It's part of a Point-Of-Sale register from Dell.
Resolution is 1024x768

TIA,

Bitphire

---

### Post by chris_nava on 2008-10-29
Having NO experience with touch screens I'll just add $0.02 ;-)
These look like calibration numbers to me.
       Option "MinX" "98"
       Option "MaxX" "1024"
       Option "MinY" "43"
       Option "MaxY" "768"
Have you tried messing with them?
If you can figure out about how far off the touch is you may be able to dead-reckon some new values.
For starters I would set MinX and MinY to 0 and see what happens.

Reminder: MAKE A BACKUP!

---

### Post by bitphire on 2008-10-29
I haven't done too much but I do have the back up of the orig xorg.conf.

Anyway,

Section "InputDevice"
        Identifier "ELO Touch"
        Driver "elographics"
        Option "Device" "/dev/tty7"
        Option "MinX" "0"
        Option "MinY" "0"
        Option "MaxX" "1024"
        Option "MaxY" "768"
        Option "UntouchDelay" "10"
        Option "ReportDelay" "10"
        Option "SendCoreEvents" "yes"
EndSection


The Device /dev/tty** just seems useless. Wrong term but I can make it ttyS0 S1 7 and it makes no difference so that is also something I'm wondering about. The MinX and Y at "0" doesn't seem to make too much of a difference that I can tell. I do know that if I slide my finger in the middle of the screen to the bottom that the mouse can go from top to bottom in about me sliding the finger and inch or two

Finger slides:
 
|
|

Mouse Moves:

|
|
|
|
|

So thinking it might also have to do with those X and Y values but I have no idea on how to get the right value to set them.

---

### Post by bitphire on 2008-10-30
Bump

---

### Post by bitphire on 2008-10-31
[https://help.ubuntu.com/community/EloIntelliTouch](https://help.ubuntu.com/community/EloIntelliTouch)

This seems to be working. Probably need to adjust the min/max XY options but still don't know how to get that value. Should I go up or down? No idea guess I'll just guess a few times.

---

