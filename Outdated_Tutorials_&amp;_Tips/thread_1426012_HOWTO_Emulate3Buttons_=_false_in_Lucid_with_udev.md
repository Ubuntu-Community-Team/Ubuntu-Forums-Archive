---
title: "HOWTO: Emulate3Buttons = false in Lucid with udev"
date: 2010-03-09
forum: Outdated Tutorials &amp; Tips
---

### Post by Rhubarb on 2010-03-09
**[SIZE="4"]Who this is for:[/SIZE]**
People running Ubuntu 10.04+ who want their mouse to register a left + right click to be 2 events (left mouse and right mouse), rather than the default of emulating a middle click.
- This is very important if you play many games, or if you simply have a middle button on your mouse and don't like the default Ubuntu behavior.

This has been tested successfully with Ubuntu 10.04 alpha 3 64bit, and should work fine after Ubuntu 10.04's formal release and both platforms (32 and 64bit).


**[SIZE="4"]A brief back story:[/SIZE]**
The new xorg in 10.04 does not depend on /etc/X11/xorg.conf or even HAL for that matter now.
So a new system of using udev gets this working quite easily and effectively.


**[SIZE="4"]Ok, let's do it!:[/SIZE]**
To get it working properly, Open up a terminal, in Applications --> Accessories --> Terminal and run the following command:
```
gksu gedit /etc/udev/rules.d/mouse-gaming.rules
```
Enter in your password when prompted, then copy and paste this into gedit:
```
ENV{x11_options.Emulate3Buttons}="False"
```
Save the file in gedit, then exit gedit.
Now all you need to do is to unplug your mouse, then plug it back in again.  The settings will have come into effect and your mouse will be good to use again for lots gaming in Lucid :)
If you're too lazy to unplug and replug your mouse in, you may alternatively run the following from a terminal:
```
sudo service udev restart
```


**[SIZE="4"]To reverse this back to the way it was:[/SIZE]**
Open up a terminal, in Applications --> Accessories --> Terminal and run the following command:
```
sudo rm /etc/udev/rules.d/mouse-gaming.rules
```
Then enter in your password if / when prompted.


**[SIZE="4"]Credits:[/SIZE]**
[LIST]
[*]I have to give thanks to pi/roman for his great tutorial [**here**]("http://ubuntuforums.org/showthread.php?p=8794054") which details the process to get a touchpad working on a laptop nicely with udev.
[*]Restarting udev is better than disconnecting and reconnecting your mouse, with thanks to tqft for his post [here]("http://ubuntuforums.org/showpost.php?p=8238390&postcount=251")
[*]Also this is in effect a continuation from my last thread [**here**]("http://ubuntuforums.org/showthread.php?t=972534") about getting it to work the old way with HAL
[/LIST]

**[SIZE="4"]Ubuntu 10.10 note:[/SIZE]**
An easier way to do this in Ubuntu 10.10 (this may work in Ubuntu 10.04, but is untested by myself):
For every new mouse that you use on your Ubuntu 10.10 system, press the middle mouse button (which on most mice all you have to do is push down on the scroll wheel).
This tells Ubuntu that you've got a middle mouse button, and hence you have no need to emulate it for that particular mouse.
This has immediate effect - no need to restart X

---

### Post by Awareness on 2010-04-05
worked like a charm :D

thanks!

This is definitely a must for ubuntu. Either you should have an option in some menu to change this, or at least the system should be able to detect if you have a third button mouse and dont activate it by default...

---

### Post by cross157 on 2010-04-12
Hi Rhubarb, perhaps you can help me with my mouse and udev. I'm trying to setup my Logitech Marble mouse using this guide for 10.04 with udev: [https://help.ubuntu.com/community/Logitech_Marblemouse_USB](https://help.ubuntu.com/community/Logitech_Marblemouse_USB)

I followed these instruction precisely but the issue is no matter what I do the mouse buttons don't behave differently. Its like the udev rule isn't taking effect. Likewise, I followed your set of commands above but the mouse behaved the same before any udev rules were setup. Any suggestions? Thanks in advance.

---

### Post by Naproxeno on 2010-05-01
I'm having the same problem, cros157. I'll try to get it to work and report back if I have any success. Anyway, help is welcome! :)

---

### Post by cross157 on 2010-05-01
Naproxeno, I never did get the udev rules to work. I opt to use xinput. Here's the code:

```
xinput set-button-map "Logitech USB Trackball" 1 2 3 4 5 6 7 8 9
xinput set-int-prop "Logitech USB Trackball" "Evdev Wheel Emulation Button" 8 8
xinput set-int-prop "Logitech USB Trackball" "Evdev Wheel Emulation" 8 1
xinput set-int-prop "Logitech USB Trackball" "Evdev Wheel Emulation Axes" 8 6 7 4 5
xinput set-int-prop "Logitech USB Trackball" "Evdev Wheel Emulation X Axis" 8 6
xinput set-int-prop "Logitech USB Trackball" "Evdev Wheel Emulation Timeout" 8 200
xinput set-int-prop "Logitech USB Trackball" "Evdev Drag Lock Buttons" 8 0
```

I have to run it each time I reboot, so I setup a shell script on the Desktop.

---

### Post by Naproxeno on 2010-05-02
Thanks, cros157!

Anyway, I think I finally got it working without having to run a script. I'll post the solution here in case somebody need it.

The [Ubuntu Community Help page]("https://help.ubuntu.com/community/Logitech_Marblemouse_USB#Ubuntu 10.04") advise you to write an udev rule to set "x11_options" but I think that's wrong. In the [Kubuntu wiki]("https://wiki.kubuntu.org/X/InputConfiguration#Driver/device options (Ubuntu 9.10)") (I use Kubuntu) the following note can be found:

> Note: The x11_options properties are not supported in Ubuntu 10.04. Use xorg.conf.d snippets instead.

So the key seem to be in these "xorg.conf.d snippets". I couldn't find much information regarding (K)Ubuntu but [this page]("https://wiki.ubuntu.com/X/Config?highlight=(xorg\.conf\.d)") seem to confirm they work in Ubuntu 10.04 and that they will be kept around at least until 10.10. The Fedora wiki has more [comprenhensive information]("https://fedoraproject.org/wiki/Input_device_configuration#xorg.conf.d").

According to Fedora, the user can place its snippets either in /etc/X11/xorg.conf.d or /usr/share/X11/xorg.conf.d. However, in Ubuntu it seems that if you put something in /etc/X11/xorg.conf.d the other directory is ignored and you can easily end up with no input devices in X. So, although putting a snippet in /usr/share/X11/xorg.conf.d should have worked, I opted for adding this to my /etc/X11/xorg.conf:

```
Section "InputClass"
        Identifier  "Marble Mouse"
        MatchProduct "ImExPS/2 Logitech Explorer Mouse"
        MatchIsPointer "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
        Option "ButtonMapping" "1 8 3 4 5 6 7 2 9"
        Option "EmulateWheel" "true"
        Option "EmulateWheelButton" "8"
        Option "ZAxisMapping" "4 5"
        Option  "XAxisMapping" "6 7"
        Option  "Emulate3Buttons" "false"
EndSection

```

Please note that my Logitech Marble Mouse is recognized as "ImExPS/2 Logitech Explorer Mouse". I have a quite old model so it could be possible for your device to have a different name. You can take a look in your Xorg log to learn its name:

```
grep Logitech /var/log/Xorg.0.log
```

Sorry for the long post. I hope it helps someone.

I'm going to update the Community Help pages to add this information.

---

### Post by lowje on 2010-05-02
I have a friend who just installed Lucid (the final realease, 32bits) and want to disable this "mouse1+mouse2=mouse3". He just did that but when he click with both button, it still emulates mouse3.

He has
$ head /etc/udev/rules.d/mouse-gaming.rules
ENV{x11_options.Emulate3Buttons}="False"

So I'm sure he did it well :/

(he unplugged/plugged, sudo service udev restart and also restart his computer)

---

### Post by Naproxeno on 2010-05-02
lowje, if the wiki is correct, I think Ubuntu currently ignores "x11_options" in udev. Perhaps your friend could try creating (or editing) /etc/X11/xorg.conf with the following content:

```
Section "InputClass"
        Identifier  "no 3 button emulation"
        MatchIsPointer "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
        Option  "Emulate3Buttons" "false"
EndSection

```

I'm not sure it would work. If your friend has any problems, he can delete that code to undo the effects.

Good luck!

---

### Post by cross157 on 2010-05-02
Naproxeno, your solution of adding Section "InputClass" to xorg.conf worked for me. Thank you.

---

### Post by lowje on 2010-05-02
Your solution works for my friend, Naproxeno. Thanks (one issue less when I will swith to Lucid ^^).

So, if I well understand, xorg.conf is not used anymore in Lucid but it  still work if we had something written on it…

---

### Post by Goatrancer on 2010-06-18
Anyone know who to disable it on a touchpad? The udev thing at the top didnt work for me and my researches show the xorg.conf is not used in Lucid. Anyone have any suggestions? My clumsy fingers keep pasting and closing tabs!

---

### Post by Konikov on 2010-12-02
> **Naproxeno said:**
> lowje, if the wiki is correct, I think Ubuntu currently ignores "x11_options" in udev. Perhaps your friend could try creating (or editing) /etc/X11/xorg.conf with the following content:

```
Section "InputClass"
        Identifier  "no 3 button emulation"
        MatchIsPointer "on"
        MatchDevicePath "/dev/input/event*"
        Driver "evdev"
        Option  "Emulate3Buttons" "false"
EndSection

```

I'm not sure it would work. If your friend has any problems, he can delete that code to undo the effects.

Good luck!


```
kern3l@Lupus ~> amdcccle
Parse error on line 7 of section InputClass in file /etc/X11/xorg.conf
        "InputClass" is not a valid section name.
Parse error on line 7 of section InputClass in file /etc/X11/xorg.conf
        "InputClass" is not a valid section name.
```

---

### Post by Goatrancer on 2010-12-02
What did you do to bring up those errors? 
I added the same lines to my (blank) Xorg file. left+right still exhibits middle click behavior.
I hope we can get to the bottom of this, I make accidentally left+right click multiple times a day, so this "feature" is a terrible annoyance for me.
It would be nice if the folks at Canonical could just tell us where to disable this "feature" in Lucid..

---

### Post by Awareness on 2010-12-03
Is there a bug report about it?

---

### Post by Rhubarb on 2011-02-01
Just to let everyone know the best way to resolve this issue (as tested on Ubuntu 10.10).

For every new mouse that you hook up to Ubuntu 10.10, press the middle mouse button (the scroll wheel) down.
- This tells Ubuntu that you indeed already have a middle mouse button on that particular mouse, and will automatically disable middle button emulation for you.

It's pretty easy, and it still catches me out every now and again, - as I don't usually press the middle mouse button at all.

---

### Post by Goatrancer on 2011-02-04
Is there some way I can trick ubuntu into thinking that I have such a mouse plugged in, while I use my built in trackpad?

This is the worst "feature" ever (at least for those of us with clumsy fingers). I can't believe there isn't a real solution yet. I am constantly closing tabs I dont want to close, pasting when I dont want to paste.

---

### Post by Rhubarb on 2011-02-08
> **Goatrancer said:**
> Is there some way I can trick ubuntu into thinking that I have such a mouse plugged in, while I use my built in trackpad?

This is the worst "feature" ever (at least for those of us with clumsy fingers). I can't believe there isn't a real solution yet. I am constantly closing tabs I dont want to close, pasting when I dont want to paste.

I don't have the time to test it, but you could try doing a 3 finger tap (if that doesn't work, try a 4 finger tap).

This 3 or 4 finger tap sends as right or middle mouse button click, and hence might just do the job.

Then again, as I haven't tested it, it may not!  - in which case you may have to find some other way of getting it working.

I totally agree, this emulating a middle mouse click by pressing L and R mouse is really annoying!

---

### Post by Goatrancer on 2011-03-05
> **Rhubarb said:**
> I don't have the time to test it, but you could try doing a 3 finger tap (if that doesn't work, try a 4 finger tap).

This 3 or 4 finger tap sends as right or middle mouse button click, and hence might just do the job.

Then again, as I haven't tested it, it may not!  - in which case you may have to find some other way of getting it working.

I totally agree, this emulating a middle mouse click by pressing L and R mouse is really annoying!

Hey thanks for the suggestion! If I just change it to something I am unlikely to do by accident that would totally take care of my problem. Now I just need to figure out this udev thing, the tutorials I've found so far haven't been terribly helpful to a person of my skill level. Anyway great idea, thanks!

---

