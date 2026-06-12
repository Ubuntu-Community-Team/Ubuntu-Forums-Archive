---
title: "Stupid freaking touchpad"
date: 2008-08-19
forum: New to Ubuntu
---

### Post by Goodkimchee on 2008-08-19
How do you disable the "if you tap them mousepad twice things launch" thingie?  It's driving me nuts.

---

### Post by OutOfReach on 2008-08-19
Goto System>Preferences>Mouse and goto the 'Touchpad' tab and disable 'Enable mouse clicks with touchpad.' :)

---

### Post by Goodkimchee on 2008-08-19
Oh right: I'm using Gutsy; is it any different?

---

### Post by OutOfReach on 2008-08-19
I don't think so. Try it out and post back if the option isn't available etc..

---

### Post by Goodkimchee on 2008-08-19
Nope, not the same.  Any suggestions?

---

### Post by tommynz1975 on 2008-08-19
I look fwd to a solution to this..  Even if some one has made a script to use a set of function keys to turn the mouse pad on and off...  I am ready to throw the lappy out the window....   

Your in the middle of  typing a command in terminal or another application and the screen changes or more scarry stuff.

---

### Post by WinterMadness on 2008-08-19
this is how i did it in Kubuntu, it might work with you.
go into the terminal:
```

sudo gedit /etc/X11/xorg.conf

```

take a look at this, find the section that looks closest to this. it should be called "InputDevice"

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
[COLOR="Red"]        Option          "MaxTapTime"            "0"[/COLOR]

see that in red? You gotta add that. make sure its lined up correctly.
If for some reason you mess up, the next time you start up it wont register you graphics card. Not to worry though theres an easy fix for that

```

locate xorg.conf

```

youll find a xorg.conf.(random numbers)

thats your back up file. So just add the contents of that into the original xorg.conf (youll have to use sudo obviously)

restart, and bam. round 2.

haha

---

### Post by Goodkimchee on 2008-08-19
Ok, not working.  Sigh... says that the command is not found...

---

### Post by Jose Catre-Vandis on 2008-08-19
it's
```
sudo nano /etc/X11/xorg.conf
```
you can replace nano with gedit if you want GUI text editor

---

### Post by Goodkimchee on 2008-08-19
Ok, I am not liking this at all.  why can't I edit the xorg.conf file?  how do I even look at it?  Argh...

> **WinterMadness said:**
> this is how i did it in Kubuntu, it might work with you.
go into the terminal:
```

sudo /etc/X11/xorg.conf

```

take a look at this, find the section that looks closest to this. it should be called "InputDevice"

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
[COLOR="Red"]        Option          "MaxTapTime"            "0"[/COLOR]

see that in red? You gotta add that. make sure its lined up correctly.
If for some reason you mess up, the next time you start up it wont register you graphics card. Not to worry though theres an easy fix for that

```

locate xorg.conf

```

youll find a xorg.conf.(random numbers)

thats your back up file. So just add the contents of that into the original xorg.conf (youll have to use sudo obviously)

restart, and bam. round 2.

haha

---

### Post by WinterMadness on 2008-08-19
> **Goodkimchee said:**
> Ok, not working.  Sigh... says that the command is not found...

whoops my bad i didnt put gedit after sudo. sorry man.

anyway, i edited my original post, go take a look at it. that should help you out!

---

### Post by Goodkimchee on 2008-08-19
Ok, I am now in the xorg.conf file, but there's no Synaptics file or section or driver.  How do I install that? What I have is

Section "InputDevice"
        Identifier       "Configured Mouse"
        Driver           "mouse"
        Option           "CorePointer"
        Option           "Device"             "/dev/input/mice"
        Option           "Protocol"           "ImPS/2"
        Option           "ZAxisMapping"       "4 5"
        Option           "Emulate3Buttons"    "true"
EndSection

Some help here would be really nice...

> **Jose Catre-Vandis said:**
> it's
```
sudo nano /etc/X11/xorg.conf
```
you can replace nano with gedit if you want GUI text editor

---

### Post by deicidist on 2008-08-19
In the Main Menu go to System> Preferences> Mouse

There should be a tab that says "Touchpad"

The second option is the one you want: "Enable mouse clicks with touchpad" Uncheck it and click "Close". That should do it!

Let me know if it doesn't. :)

---

### Post by Goodkimchee on 2008-08-19
Nope, i do not have that option tab available to me.  If I did, this would be a very short thread!  :)

> **deicidist said:**
> In the Main Menu go to System> Preferences> Mouse

There should be a tab that says "Touchpad"

The second option is the one you want: "Enable mouse clicks with touchpad" Uncheck it and click "Close". That should do it!

Let me know if it doesn't. :)

---

### Post by WinterMadness on 2008-08-19
> **Goodkimchee said:**
> Ok, I am now in the xorg.conf file, but there's no Synaptics file or section or driver.  How do I install that? What I have is

Section "InputDevice"
        Identifier       "Configured Mouse"
        Driver           "mouse"
        Option           "CorePointer"
        Option           "Device"             "/dev/input/mice"
        Option           "Protocol"           "ImPS/2"
        Option           "ZAxisMapping"       "4 5"
        Option           "Emulate3Buttons"    "true"
EndSection

Some help here would be really nice...

I find it weird that you cant goto the system menu and do it like everyone else suggested. but anyway as long as you follow my directions to fix it if you mess up you can try the maxtaptime thing.

---

### Post by AClark on 2008-08-19
> **Goodkimchee said:**
> How do you disable the "if you tap them mousepad twice things launch" thingie?  It's driving me nuts.

I installed Qsynaptics on a Gutsy machne.  Nice little gui applicaton that lets you confgure your touchpad - although the only option I use is the "Off" button.

Info here:
[http://www.ubuntu1501.com/2007/04/configure-synaptic-touchpad-settngs.html](http://www.ubuntu1501.com/2007/04/configure-synaptic-touchpad-settngs.html)

It worked for me.

---

