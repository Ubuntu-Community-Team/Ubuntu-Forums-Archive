---
title: "Desktop &quot;too big&quot; for my screen"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by taouz on 2008-07-20
HI.  I've just installed Hardy, and it's my first Linux distro ever.  I'm using my 32" Fujitsu Siemens Myrica V32-1 as a monitor.  I have a GeForce 4200 graphics adapter.

The problem is, that I'm not able to adjust the resolution to the one I want, and the one I have makes the desktop "too big" for my screen, meaning that I can't see the Menu lines neither on top or bottom, and also on the sides it's cut.  

I've tried searching for solutions, tried editing my xorg.conf and installing nVidia drivers and so on, but still no luck.  

EDIT:
The resolution I have now, is 1280x720, but the I want, and the one I have had with f.eks WinXP, is 1366x768 (overscanning of the LCD display).

I don't understand why it can't display the whole desktop when the resolution I have is smaller than what my monitor supports, and why I can't adjust it.  It seems like changes made to xorg.conf are ignored, or maybe I'm doing it wrong.

Here is my xorg.conf. The way it is now. I've tried adding a modeline, but aren't really sure how, and have just tried different things seen around the web.  Doesn't seem to help, though, and I'm not able to choose this setting in my settings.

> Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard" "CoreKeyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "no"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1368x765_60"
    EndSubSection
EndSection

A big bucket of Popcorn to anyone helping me to solve this! :popcorn:

---

### Post by t0p on 2008-07-20
Sorry I can't help you resize your desktop.

But in the meantime, if you want to get at the bits that are off-screen, you'll be able to drag the desktop around by holding down **Alt** and your right mouse button while moving your mouse.

---

### Post by nickftm on 2008-07-20
I've had the same problem as you in the past. Try this. Install nvidia-settings from Synaptic (System > Administration > Synaptic Package Manager), or just type this in a terminal (Applications > Accessories > Terminal):

```
sudo apt-get install nvidia-settings
```

Then type in a terminal window:

```
gksudo nvidia-settings
```

See if that program will let you set your resolution right. Don't forget to press the 'Save to X configuration file' button if it works.

---

### Post by billgoldberg on 2008-07-20
It might be a long shot, but try pressing the button on the monitor that "syncs" (for the lack of a better word) your desktop.

It worked for me.

The icons looks like a screen with 4  things like _|  in it on the corners and a + in the middle.

---

### Post by taouz on 2008-07-20
> **nickftm said:**
> I've had the same problem as you in the past. Try this. Install nvidia-settings from Synaptic (System > Administration > Synaptic Package Manager), or just type this in a terminal (Applications > Accessories > Terminal):

```
sudo apt-get install nvidia-settings
```

Then type in a terminal window:

```
gksudo nvidia-settings
```

See if that program will let you set your resolution right. Don't forget to press the 'Save to X configuration file' button if it works.

Well. I tried this, but still it doesn't work.  I don't get the option of 1368x765 that I want.  

Anyone else?

PS.  I can't seem to get the ALT+right button to work either.

---

### Post by philinux on 2008-07-20
One thing to try is "screens and graphics"

It's hidden in Other.

Use System Prefs Main Menu to enable the menu item.

The other is boot up and press esc at grub and select recovery mode

At the menu choose xfix.

---

### Post by lukjad on 2008-07-20
Here are a few things that may work for you:
[INDENT]1) Sometimes the screen itself is at fault. There are usually buttons that lead to the horizontal and vertical sizes. Try manipulating them so that your screen doesn't overlap. After that play around with step 2 to make it look better.

2) Go to System->Preferences->Screen Resolution and try changing it from there. Sometime you need to do both steps 1 and 2 to make the screen look good. I hope this works for you.

3) There used to be a way to add a screen resolution to the xorg.conf file but I seem to have either forgotten how or they have changed where the screen resolutions are put. (If someone out there knows how, please post.)
[/INDENT]

I hope these things work for you.

---

### Post by little_penguin on 2008-07-20
Try adding the following line "Virtual 1368 765" in the "Display" subsection of your xorg.conf file:

Section "Screen"
Identifier "Default Screen"
Device "Configured Video Device"
Monitor "Configured Monitor"
DefaultDepth 24
Option "AddARGBGLXVisuals" "True"
Option "NoLogo" "True"
SubSection "Display"
**Virtual 1368 765**
Depth 24
Modes "1368x765_60"
EndSubSection
EndSection

This usually works for me, I hope it helps you out.
Regards, LP

---

### Post by t0p on 2008-07-20
> **taouz said:**
>  I can't seem to get the ALT+right button to work either.

Whoops!! That should have been Alt + **Left** button!

Terribly sorry!

---

