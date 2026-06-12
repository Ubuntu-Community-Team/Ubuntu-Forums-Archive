---
title: "Xubuntu Laptop Touchpad Problem"
date: 2008-08-22
forum: New to Ubuntu
---

### Post by magwhyte on 2008-08-22
When I was using Ubuntu 8.04, it was extremely easy to turn off the touchpad on my Compaq Presario C500.  However, in Xubuntu, I am unable to find out how to turn it off.

Unfortunately, with the Touchpad turned on, it is extremely difficult to type anything on the keyboard without me accidentially adding/deleting or just plain moving the cursor onto other parts of the webpage.

Any advice/guidance would be really appreciated.

Adrian

---

### Post by seagullplayer77 on 2008-08-23
I have an HP dv9000 series laptop, and while I can turn the touchpad off and on without any problem, whenever I press the button to enable the touchpad, Ubuntu Help launches as well. Assuming that you have a button to enable/disable the touchpad, does anything at all happen when you press it?

---

### Post by magwhyte on 2008-08-23
Sorry for the delay in responding, but I don't see a button to turn on/turn off the touchpad.

Thanks...

Adrian

---

### Post by mettlewk on 2008-09-03
Ok, I just identified my cursor jumping problem as poor typing technique.:lolflag:

All my problems should be so simple.

The advice was turn of the touchpad, yeah but HOW!

I figured I might just - - -

Explore the menus  

Think geeeeee where might that control be?????

Lets' see there is a menu item here that says System....

that looks like a good bet.

Ok, I'd prefer not to have the touchpad work... That sounds like a personal preference not an administrative decision, there might be another user that likes it so Preferences looks like a good bet.

Oh great, here is an item for the Mouse maybe that will have some information I could use. 

Well look at that, there are three tabs, and one says "touchpad" 

There is a checkbox that says: Enable touchpad and it is checked already.

I want if off. What happens if I uncheck it. 

Bingo.

Such was my adventure a couple minutes ago, and it took less time than reading this silly post.

Thanks for the help guys.

Gene

---

### Post by wladicus on 2008-09-11
Quoted my mettlewk
"There is a checkbox that says: Enable touchpad and it is checked already.
I want if off. What happens if I uncheck it.  Bingo."
---------------
That sounds great!, but alas there is no such method available in Kubuntu.  I have tried everything, many suggestions from you kind folks, and still, NO ONE seems to be able to figure this out.  No one has taken up my challenge on other posts either.
I would be most thankful if someone figured this out for Kubuntu.  One small thing like this can ruin the whole Linux experience.  Is the Linux Kubuntu team admitting defeat?
Well thank you for your help thus far anyway.
walt

---

### Post by kjohansen on 2008-09-11
I turned off the tap of my touchpad with an option in my xorg.conf file.

In /etc/X11/xorg.conf find your Input device section for your touchpad and add the MaxTapTime option.  A copy of mine is included for reference.

```

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizEdgeScroll" "0"
    Option         "MaxTapTime" "0"
EndSection

```

---

### Post by wladicus on 2008-09-12
[QUOTE=kjohansen 5772335]I turned off the tap of my touchpad with an option in my xorg.conf file...add the MaxTapTime option.[/QUOTE]
kjohansen I thank you kindly for trying to help with your suggestion. I am sure it works on many machines.  This, in fact, was amongst the very first things that were suggested, and I tried all of them.  They do not want to work on my machine. :(
As I mentioned before, my machine does NOT have a Synaptics touchpad.  It is a MDG VisionBook with 3GB of RAM and has a Logitech touchpad, and I do not know if this has anything to do with it.  The xorg.conf file has the same code as you have indicated and I have no idea why this code appears in my xorg.conf file, since my touchpad is NOT a Synaptics touchpad.  No one has been able to explain how or why this happens.  I am beginning to think that this file is a generic build and Kubuntu has no idea of how to correctly assess my touchpad and mouse configuraton.  I do not experience any of these problems running Windows Vista on the same machine.
Please help if it is possible to do so! :confused:
Thank you again for ongoing suggestions and moral support. :):KS
walt

---

### Post by wladicus on 2008-09-17
****** SOLVED FINALLY ******
From a terminal enter the following code:
To disable the Touchpad -
```
sudo rmmod psmouse
``` 
To re-enable a disabled Touchpad -
```
sudo modprobe psmouse
``` 
I suppose this can be automated in a file somehow or even attached to a function key probably if someone has the knowhow.
I received this solution from the following link:

[http://ubuntuforums.org/showpost.php?p=5694509&postcount=13](http://ubuntuforums.org/showpost.php?p=5694509&postcount=13)

A detailed HOW TO for setting up a shortcut key version of this can be found in the last post at the following link:
>    [http://forums.techguy.org/unix-linux/746623-solved-deactivating-touchpad-kibuntu.html](http://forums.techguy.org/unix-linux/746623-solved-deactivating-touchpad-kibuntu.html)  

---

### Post by Insomn1a on 2008-11-16
> **wladicus said:**
> ****** SOLVED FINALLY ******
From a terminal enter the following code:
To disable the Touchpad -
```
sudo rmmod psmouse
``` 
To re-enable a disabled Touchpad -
```
sudo modprobe psmouse
``` 
I suppose this can be automated in a file somehow or even attached to a function key probably if someone has the knowhow.
I received this solution from the following link:

[http://ubuntuforums.org/showpost.php?p=5694509&postcount=13](http://ubuntuforums.org/showpost.php?p=5694509&postcount=13)

A detailed HOW TO for setting up a shortcut key version of this can be found in the last post at the following link:


man finally someone has a solution other then editing a synaptics section that i dont have,   

thank you very much for that, its greatly appreciated.

---

