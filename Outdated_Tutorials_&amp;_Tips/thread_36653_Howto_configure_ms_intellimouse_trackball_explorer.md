---
title: "Howto configure ms intellimouse trackball explorer"
date: 2005-05-24
forum: Outdated Tutorials &amp; Tips
---

### Post by blakken on 2005-05-24
2 years!Took me two bloody years to finally realize it was as simple as this to have all my buttons supported under xorg (previously xfree) .Throught all the internet sites none of them were referencing this config and supporting this trackball! I suppose I'm far from being this only one using it under linux.
Let's make this simple,no point on adding imwheel package ,not even xmodmap.
SImply follow this:
in /etc/X11 change xorg.conf ,go to section Inputdevice and do those modifications:

Section "InputDevice"
 Identifier "Configured Mouse"
 Driver  "mouse"
 Option  "CorePointer"
 Option  "Device"  "/dev/input/mice"
 Option  "Protocol"  "ExplorerPS/2"
 Option  "Emulate3Buttons" "true"
 Option  "ZAxisMapping"  "4 5"
 Option          "Buttons"               "7"
EndSection

Et Voilà!
right side buttons  work perfectly as previous and forward under mozilla!
Restart xorg and under console start xev you should see while clicking:

*for button 6:

KeymapNotify event, serial 30, synthetic NO, window 0x0,
    keys:  69  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0

ButtonRelease event, serial 30, synthetic NO, window 0x2a00001,
    root 0x45, subw 0x2a00002, time 960673, (54,39), root::(56,659),
    state 0x0, button 6, same_screen YES

LeaveNotify event, serial 30, synthetic NO, window 0x2a00001,
    root 0x45, subw 0x0, time 960673, (54,39), root::(56,659),
    mode NotifyUngrab, detail NotifyInferior, same_screen YES,
    focus YES, state 0

*for button 7:

KeymapNotify event, serial 30, synthetic NO, window 0x0,
    keys:  69  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0

ButtonRelease event, serial 30, synthetic NO, window 0x2a00001,
    root 0x45, subw 0x2a00002, time 956858, (54,39), root::(56,659),
    state 0x0, button 7, same_screen YES

LeaveNotify event, serial 30, synthetic NO, window 0x2a00001,
    root 0x45, subw 0x0, time 956858, (54,39), root::(56,659),
    mode NotifyUngrab, detail NotifyInferior, same_screen YES,
    focus YES, state 0

  \\:D/

---

### Post by Spike on 2005-06-01
Thank you. That works.

Any idea how I can:
a) Have my scroll wheel scroll a page at a time?
b) Have pressing my scroll wheel initiate a double-click?

ty in advance.

---

### Post by JediCowboy on 2005-10-24
Ye Gods!  It worked on my Intellimouse Explorer side buttons and the scroll still works!   I've tried imwheel, yadda yadda yadda, nothng.  Just cutting and pasting this text worked for me.  Thanks!

Only one minor quibble - I can't close a Firefox Beta 2 tab with a middle click like I used to, but compared to gaining the FWD/BK buttons, I can live with it.  Still, would anyone have a clue how to enable the middle click on Firefox?

---

### Post by bleiddyn on 2007-04-30
This is good info, but is there a way anyone knows of to map the buttons elsewhere?  (I find it easier if the top-left is paste, and the bottom right is copy, with the top-right being right-click.)

Going to continue mucking about in this one, but if someone knows...

---

### Post by highspider on 2010-12-14
MS intelliMouse  (the wireless one with side buttons)
FOR ALL the buttions to work; edit /etc/X11/xorg.conf   
**NOTE: the button mapping includes for side buttons to do "forward" and and "back" in like firefox / 
               SeaMonkey and no restart is required
NOTE: Tested on Ubuntu 10.04 LTS - the Lucid Lynx - released in April 2010
             but should work fine with past version.
REM  : Allows remember with cut and past from message boards to check your " and ' because some
            times they transfier as other ASCII keys that look the same :)  

devil@hell:~$ sudo gedit /etc/X11/xorg.conf   
or 
devil@hell:~$ sudo nano /etc/X11/xorg.conf   


Section "InputDevice"
        Identifier "Configured Mouse"
        Driver "mouse"
        Option "CorePointer"
        # Option "Device" "/dev/input/mice"
        Option "Protocol" "ExplorerPS/2"
        Option "Emulate3Buttons" "false"
        Option "ZAxisMapping" "4 5"
        Option "ButtonMapping" "1 2 3 6 7"
EndSection

---

