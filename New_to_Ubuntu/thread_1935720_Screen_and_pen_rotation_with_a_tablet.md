---
title: "Screen and pen rotation with a tablet"
date: 2012-03-04
forum: New to Ubuntu
---

### Post by peterson43 on 2012-03-04
I am running Ubuntu 11.10 on a Thinkpad X61 Tablet. I used the instructions at [http://www.thinkwiki.org/wiki/Installing_Ubuntu_10.04_%28Lucid_Lynx%29_on_a_ThinkPad_X61_Tablet#Rotate:]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_10.04_%28Lucid_Lynx%29_on_a_ThinkPad_X61_Tablet#Rotate:") 
to get the screen rotation button working. However, when I rotate the screen, the pen doesn't rotate with it. For instance, if the screen has been rotated 180 degrees, when I put the pen in the top left of the screen the cursor still shows up in the old top left (my bottom right). It makes using the pen essentially useless when the screen is rotated. 

Does anyone know how to fix this?

---

### Post by Favux on 2012-03-04
It sounds like whatever script you have bound to the rotation button is not using the proper "device names" in the xsetwacom rotation commands to rotate the input tools like the stylus.  You can get the "device names" from the output of the *xinput list* command in a terminal.  Then just correct the script.

For automatic rotation also see the [Rotation HOW TO]("http://ubuntuforums.org/showpost.php?p=6274392&postcount=1") and [Magick Rotation]("https://launchpad.net/magick-rotation").

---

### Post by peterson43 on 2012-03-04
As far as I can tell, the instructions I followed had be create a script called "rotatebutton" that used the xrandr command to rotate the screen. (I checked that doing the xrandr commands from the terminal also didn't rotate the pen correctly). I don't know how to edit the xsetwacom commands for the xrandr command (nor if this is a smart idea).

---

### Post by Favux on 2012-03-04
The xrandr commands rotate the screen orientation.  You then have to use xsetwacom commands to rotate the stylus, eraser, and touch (if you have it) along with the change in screen orientation.  What does the rotation script you have bound to the rotation button look like?

---

### Post by peterson43 on 2012-03-05
> **Favux said:**
> The xrandr commands rotate the screen orientation.  You then have to use xsetwacom commands to rotate the stylus, eraser, and touch (if you have it) along with the change in screen orientation.  What does the rotation script you have bound to the rotation button look like?

The "rotatebutton" command that I copied from the above mentioned source looks like

```
mode=`cat /usr/bin/rotationmode`
if test 0 = $mode
then
echo 1 > /usr/bin/rotationmode
xrandr -o right
fi
if test 1 = $mode
then
echo 2 > /usr/bin/rotationmode
xrandr -o inverted
fi
if test 2 = $mode
then
echo 3 > /usr/bin/rotationmode
xrandr -o left
fi
if test 3 = $mode
then
echo 0 > /usr/bin/rotationmode
xrandr -o normal
fi
```

It appears to be a pretty simple script. The file /usr/bin/rotationmode just keeps track of what orientation the screen currently is in and the script simply rotates the screen to the "next" orientation and updates the rotationmode file accordingly (at least that's what I think it does). Do I need to add a xsetwacom command somewhere in this script? If so, what should I add?

---

### Post by Favux on 2012-03-05
Right, there aren't any xsetwacom commands.  See the method 1 scripts on the Rotation HOW TO to see what I mean.  This script is designed to be used with Tom Jaeger's wacomrotate daemon, that's what is missing.  It rotates the screen and wacomrotate rotates the wacom stuff.

I don't know if wacomrotate still works for Oneiric.  I don't remember checking if Tom updated it recently.  It is also in the Rotation HOW TO as method 4.

---

### Post by peterson43 on 2012-03-06
> **Favux said:**
> Right, there aren't any xsetwacom commands.  See the method 1 scripts on the Rotation HOW TO to see what I mean.  This script is designed to be used with Tom Jaeger's wacomrotate daemon, that's what is missing.  It rotates the screen and wacomrotate rotates the wacom stuff.

I don't know if wacomrotate still works for Oneiric.  I don't remember checking if Tom updated it recently.  It is also in the Rotation HOW TO as method 4.

The instructions I had followed previously had me install wacomrotate, but I'm not sure why since the script didn't seem to implement it. 

Anyway, I was able to follow the instructions in the Ration HOW TO in method 1 (and the remarks at the beginning) to figure out how to modify my script to get it to work. The modified script is as follows. 

```
mode=`cat /usr/bin/rotationmode`
if test 0 = $mode
then
echo 1 > /usr/bin/rotationmode
xrandr -o right
xsetwacom set "Serial Wacom Tablet stylus" rotate ccw
xsetwacom set "Serial Wacom Tablet touch" rotate ccw
xsetwacom set "Serial Wacom Tablet eraser" rotate ccw
fi
if test 1 = $mode
then
echo 2 > /usr/bin/rotationmode
xrandr -o inverted
xsetwacom set "Serial Wacom Tablet stylus" rotate half
xsetwacom set "Serial Wacom Tablet touch" rotate half
xsetwacom set "Serial Wacom Tablet eraser" rotate half
fi
if test 2 = $mode
then
echo 3 > /usr/bin/rotationmode
xrandr -o left
xsetwacom set "Serial Wacom Tablet stylus" rotate cw
xsetwacom set "Serial Wacom Tablet touch" rotate cw
xsetwacom set "Serial Wacom Tablet eraser" rotate cw
fi
if test 3 = $mode
then
echo 0 > /usr/bin/rotationmode
xrandr -o normal
xsetwacom set "Serial Wacom Tablet stylus" rotate none
xsetwacom set "Serial Wacom Tablet touch" rotate none
xsetwacom set "Serial Wacom Tablet eraser" rotate none
fi

```

---

### Post by GoodPanos on 2012-06-03
Every time I run the above script I get:
```
line 2: test: too many arguments
```
I get this for each line there is a "if x = $mode"

Any thoughts?

---

### Post by Favux on 2012-06-03
Hi GoodPanos,

Which tablet PC do you have?

What is the output in a terminal of?
```
cat /usr/bin/rotationmode
```

---

### Post by GoodPanos on 2012-06-17
Sorry for the long delay.

Lenovo Thinkpad X61 Tablet

It just returns "0" (without the quotes)

---

### Post by Favux on 2012-06-19
The number should change from 0 for laptop to either 1, 2, or 3 for the two portrait modes and inverted according to the script.  Since you are using the echo command to modify the file I'm not sure where the too many arguments are coming from unless you have a typo?


You can get a binary 0 for laptop or 1 for tablet mode.
```
cat /sys/devices/platform/thinkpad_acpi/hotkey_tablet_mode
```
That's what the "Method 2: Tablet PC Automatic Rotation Script" script is based on in the [Rotation HOW TO]("http://ubuntuforums.org/showthread.php?t=996830").

Seems like there was a syntax change.  Maybe it is suppose to be:
```
if test 0 = $(mode)
```
or something?

---

### Post by GoodPanos on 2012-06-19
First line returns "0" and second line even worst errors :-?

---

### Post by GoodPanos on 2012-06-20
Ok, I tried Method 1 from your HowTo and the screen is rotating.  Can you in simple steps (sorry, I got completely lost with that section) how to bind that script file to the bezel button.  I found the keycode to be 199.

---

### Post by Favux on 2012-06-20
Hmm.  Maybe ($mode)?  Have to look up test and see if its changed or whatever.

I assume you have the script you want ready and have run through the steps in **a) script**?

Alright the keycode from the rotation bezel button is 199.  Pressing it doesn't do anything but make 199 appear in xev, correct?  If so we can try a couple of things.

But first I don't think you have mentioned which Ubuntu release you are using.  Does your release use compiz and do you have the CompizConfig Settings Manager (CCSM) installed?

---

### Post by GoodPanos on 2012-06-20
...and I figured that one out too. :D

I have Xubuntu which was quite easy to do the assignment.

Thank you for sticking around, I really appreciate your help.

Ok, this thread is truly solved.

---

### Post by Favux on 2012-06-20
Great!  :)

For the benefit of others do you mind posting what you did in Xubuntu to get the key binding assignment working?

---

