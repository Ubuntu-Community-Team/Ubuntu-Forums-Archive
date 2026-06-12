---
title: "HOW TO:  Laptop Touchpad"
date: 2004-11-11
forum: Outdated Tutorials &amp; Tips
---

### Post by DoubleDangerClub on 2004-11-11
What everyone has been waiting for:

Laptop Touchpad How-To
----------------------------------------------------------
This How-To guide applies to all PS2 and Serial synaptics touchpads as far as I can tell.  We have not found this to work for emulated USB cPads (Synaptics cPad).  Other than that...

Open a terminal window and type: ```
sudo gedit /etc/X11/XF86Config-4
```

Go to the section: ```
Section "Module"
```
Add this line inside this section: ```
Load "synaptics"
```

This line loads your synaptics touchpad settings at startup.
Now, as you scroll down, there should be a section that starts like this:

```
Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
```

In this section, delete the line that says: ```
Option "CorePointer"
```
This will make sense later on, as the external mouse will be secondary to the touchpad.

As you scroll down further, you should see this section:

```
Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
EndSection
```

Delete the line that says: ```
Option "SendCoreEvents"
```
Add a line that says: ```
Option "SHMConfig" "on"
```
The line you deleted will make sense later, as we will make the touchpad the primary pointer device.
The additional line enables your touchpad settings.

Finally scroll down to the bottom and you'll see this section:

```
Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
InputDevice "Synaptics Touchpad"
EndSection
```

Change the last two lines to look like this:
```
InputDevice "Configured Mouse" "SendCoreEvents"
InputDevice "Synaptics Touchpad" "CorePointer"
```

These additions will make the system set the touchpad to the primary pointer device and the external mouse as the secondary device.

Save the file and reboot!


You thought it was over? Almost. We now want to set our settings:
If you open a terminal window and type: ```
synclient -l
```
This shows you all of your touchpad settings.
If you reset any of the settings, you will lose them when you log out, so what we need to do is open the config file again:

```
sudo gedit /etc/X11/XF86Config-4
```

Now, scroll down to the section that starts like this:

```
Section "InputDevice"
Identifier "Synaptics Touchpad"
```

Inside this section, you will want to add your settings.
Open another terminal window and type: ```
synclient -l
```
Now look at the setting you would like to change (I'm going to demonstrate turning off the tap click and the vertical and horizontal scrolling on the side and bottom of the touchpad). Look at the name of the setting and enter it in this fashion:

```
Option "MaxTapTime" "0"
Option "VertScrollDelta" "0"
Option "HorizScrollDelta" "0"
```

Now save your file and reboot. All done!!

If you go out on the net, you can find more references to synclient. I have even caught wind of a GUI version of the settings manager, but this is the most effective way I found to get it done.

I hope this helps. I was frustrated and finally figured it out, so good luck, and if you have questions about it, feel free to message me.

- Jake a.k.a. DoubleDangerClub

---

### Post by FLeiXiuS on 2004-11-11
Excellent how to!

---

### Post by DoubleDangerClub on 2004-11-11
[QUOTE=FLeiXiuS]Excellent how to![/QUOTE]

Thank you.  I forgot to add [CODE] blocks.  I'll go back in tomorrow and edit them.

---

### Post by gunnar_steinn on 2004-11-11
Hi

I'm still having trouble with my touchpad after following your how-to, in fact nothing changed.

The touchpad seems to work with the exception of I can't move the mouse. I can click, double click  (both on the touchpad it self and the buttons below) and right click with no troubles.

I tried Ubuntu live cd and the mouse worked there without troubles which makes this strange.

Here are my synclient settings. The XFree86 settings are as in the how-to

gsm@wnn0617:~ $ synclient -l
Parameter settings:
    LeftEdge             = 1900
    RightEdge            = 5400
    TopEdge              = 1900
    BottomEdge           = 4000
    FingerLow            = 25
    FingerHigh           = 30
    MaxTapTime           = 180
    MaxTapMove           = 220
    MaxDoubleTapTime     = 180
    ClickTime            = 100
    EmulateMidButtonTime = 75
    VertScrollDelta      = 100
    HorizScrollDelta     = 100
    MinSpeed             = 0.02
    MaxSpeed             = 0.18
    AccelFactor          = 0.0015
    EdgeMotionMinZ       = 30
    EdgeMotionMaxZ       = 160
    EdgeMotionMinSpeed   = 1
    EdgeMotionMaxSpeed   = 200
    EdgeMotionUseAlways  = 0
    UpDownScrolling      = 1
    TouchpadOff          = 0
    GuestMouseOff        = 0
    LockedDrags          = 0
    RTCornerButton       = 2
    RBCornerButton       = 3
    LTCornerButton       = 0
    LBCornerButton       = 0
    TapButton1           = 1
    TapButton2           = 2
    TapButton3           = 3
    CircularScrolling    = 0
    CircScrollDelta      = 0.1
    CircScrollTrigger    = 0



any ideas?

thanks
Gunnar Steinn

---

### Post by Magneto on 2004-11-11
Gunnar -  My synaptics touchpad worked out of the box on Ubuntu's default installation and my already configure XF86Config-4 file. I am using a Dell Latitude though.
Are you using the default ubuntu kernel? If not make sure you have the right event interface settings enabled.

---

### Post by DoubleDangerClub on 2004-11-11
Gunnar...
I see your settings haven't changed, did you hardcode any changes to them in the XF86Config-4 file?
I also found that if you don't delete the "CorePointer" line from the external mouse section, it will cause the no mouse moving problem.  You might (if you only use the touchpad) delete the "SendCoreEvents" code after the "Configured Mouse" line in the "Server Layout" section.

One more thing to help...in the "Input Device" section for the Synaptics Touchpad...make sure that the name in quotes after "Driver" is the same name used in the "Load" line of the Module Section, as well as the same name as the line in the Server Layout section.

I hope that helps you.

-DDC

---

### Post by gunnar_steinn on 2004-11-12
Hi, thanks for your very fast responses! :)

Magneto: I haven't changed the kernel at all. I followed the howto on adding debian universe and did an upgrade after that but I think the kernel didn't change.

gsm@wnn0617:~ $ uname -a
Linux wnn0617 2.6.8.1-3-386 #1 Tue Oct 12 12:41:57 BST 2004 i686 GNU/Linux

DoubleDangerClub: I double checked everything you said and it seems allright. I also tried to remove the "SendCoreEvents" and that resulted in no change except my external mouse didn't work after I plugged it in.

I put the logs and configs at [http://gunnarsteinn.com/ubuntu](http://gunnarsteinn.com/ubuntu) (I didn't want to flood this thread), if you could check if this looks right :)

Is there a program or a log that can output the info from the touchpad? Just to see if we get any input from it.
Also, is there any other driver that could work as a replacement until this works out? Some generic touchpad driver?

Thanks
Gunnar Steinn

---

### Post by gunnar_steinn on 2004-11-12
Okey, to answer my own question if there was a program that could monitor the touchpad... of course the synclient does that.

gsm@wnn0617:~ $ synclient -h
Hardware properties:
    No touchpad found
    Do you use a newer kernel than 2.4?
    Then browse the messages or boot.msg for the hardware info

So it seems it doesn't find the touchpad but running
"synclient -m 2" displays events when I tap the touchpad but not when I try to move the mosue (so there is something alive at least)

I will try to find something in the dmesg or boot.msg

Gunnar Steinn

---

### Post by DoubleDangerClub on 2004-11-12
Your files are looking fine, but the thing that I did notice that is different to me is in your hardware manager.
It shows on your system that the synaptics touchpad is a sort of USB device.  When I went into my hardware manager, I couldn't even find my synaptics touchpad mentioned anywhere.  Anyhow, I noticed that it called it: synaptics cPad.

I looked into it more and it seems that they have 3 types of touchpads...Serial, PS2, and emulated USB (the cPad, which is yours).  I found a site that may help you.

[http://www.janerob.com/rob/ts5100/cPad/JanS/cpad.html](http://www.janerob.com/rob/ts5100/cPad/JanS/cpad.html)

Also, I would suggest looking on google for 'Synaptics cPad.'  I'm sure there is a resource that can aid you as well.  I'm sorry my guide wasn't able to help you out.  Was your mouse moving before my guide?  If so, alter your files back to their original state and search for some cPad help. :)  I hope this helped.

- DDC

---

### Post by gunnar_steinn on 2004-11-12
The mouse never worked so you didn't break anything.

The mouse works now after some rmmod/insmod stuff with usbhid, usbmouse, ohci1394. I'm not completely sure what I did but I'm sure it will break after restart.
I will post the solution when I will find it.

Thanks!
Gunnar Steinn

---

### Post by Magneto on 2004-11-12
[QUOTE=gunnar_steinn]The mouse never worked so you didn't break anything.

The mouse works now after some rmmod/insmod stuff with usbhid, usbmouse, ohci1394. I'm not completely sure what I did but I'm sure it will break after restart.
I will post the solution when I will find it.

Thanks!
Gunnar Steinn[/QUOTE]
u loaded the drivers your kernel needed in order to use your usb based touchpad properly - there's a way to make sure those modules always get loaded at startup

---

### Post by Mischa on 2005-01-23
i had to install synaptec also ,else x did not start obviously:)
 
 sudo apt-get install xfree86-driver-synaptics
 
 might want to add that at the beginning of you howto :)
 
 cya,
 
    mischa

---

### Post by riverfr0zen on 2006-03-01
Here's a heavily commented synaptics config - should be useful for those who don't know what each setting is for.

From [http://www.jl42.de/linux/config/xorg.conf]("http://www.jl42.de/linux/config/xorg.conf")

```
Section "InputDevice"
        Driver          "synaptics"
        Identifier      "Touchpad"
	Option		"CorePointer"
        Option          "Device"        "/dev/input/event1"
        Option          "Protocol"      "auto-dev"
	# switch on/off shared memory for configuration
        Option          "SHMConfig"		"on"
	# coordinates of the edges
	Option		"LeftEdge"              "120"
	Option		"RightEdge"             "855"
	Option		"TopEdge"               "120"
	Option		"BottomEdge"            "650"
	# When finger pressure drops below this value,
	# the driver counts it as a release.
	Option		"FingerLow"             "14"
	# When finger pressure drops below this value,
	# the driver counts it as a release.
	Option		"FingerHigh"            "15"
	# max. time (in milliseconds) for detecting a tap
	Option		"MaxTapTime"            "180"
	# max. movement of the finger for detecting a tap
	Option		"MaxTapMove"            "110"
	# max. time (in milliseconds) for detecting a double tap
        Option          "MaxDoubleTapTime"      "100" #
	# the duration of the mouse click generated by tapping
        Option          "ClickTime"             "130" #
	# move distance of the finger for a scroll event
        Option          "VertScrollDelta"       "100"
        Option          "HorizScrollDelta"      "100"
	# finger pressure at which minimum edge motion speed is set
	Option		"EdgeMotionMinZ"   	"30"
	# finger pressure at which maximum edge motion speed is set
	Option		"EdgeMotionMaxZ"   	"100"
	# slowest setting for edge motion speed
	Option		"EdgeMotionMinSpeed"	"12"
	# fastest setting for edge motion speed
	Option		"EdgeMotionMaxSpeed"	"20"
	# If on, edge motion is also used for normal movements,
	# if off, egde motion is used only when dragging
	Option		"EdgeMotionUseAlways"	"off"
	# repeater device
        Option          "Repeater"      "/dev/input/event1"
	# min./max. speed factor
        Option          "MinSpeed"      "0.35" #
        Option          "MaxSpeed"      "1" #
	# acceleration factor
        Option          "AccelFactor"   "2.0" #
	# If on, the up/down buttons generate button 4/5 events.
	# If off, the up button generates a double click and
	# the down button generates a button 2 event.
        Option          "UpDownScrolling"       "on"
	# max time (in milliseconds) for middle button emulation.
        Option          "EmulateMidButtonTime"  "75"
	# If on, the Touchpad is switched off
	# (useful if an external mouse is connected)
	Option		"TouchpadOff"		"off"
	# switch on/off guest mouse (often a stick)
	Option		"GuestMouseOff"		"off
	# If off, a tap and drag gesture ends when you release the finger.
	# If on, the gesture is active until you tap a second time.
	Option	 	"LockedDrags"		"on"
	# Which mouse button is reported on a top corner tap
	# (RT right top, RB right bottom, LT left top, LB left bottom)
	# 0=No action, 1=Left Button, 2=Middle Button, 3=Right Button
        Option          "RTCornerButton"        "0"
        Option          "RBCornerButton"        "0"
        Option          "LTCornerButton"        "2"
        Option          "LBCornerButton"        "2"
	# Which mouse button is reported on a non-corner
	# (one|two|three)-finger tap.
	# 0=No action, 1=Left Button, 2=Middle Button, 3=Right Button
        Option          "TapButton1"            "1"
        Option          "TapButton2"            "2"
        Option          "TapButton3"            "3"
	# If on, circular scrolling is used (see below)
	Option		"CircularScrolling" 	"off"
	# Move angle (radians) of finger to generate a scroll event
	Option		"CircScrollDelta"  
	# Trigger region on the touchpad to start circular scrolling
	# 0=All Edges, 1=Top Edge, 2=Top Right Corner, 3=Right Edge, 4=Bottom Right Corner,
	# 5=Bottom Edge, 6=Bottom Left Corner, 7=Left Edge, 8=Top Left Corner
	Option		"CircScrollTrigger"
	# Instead of being a rectangle, the edge is the ellipse
	# enclosed by the Left/Right/Top/BottomEdge parameters.
	# For circular touchpads.
	Option	        "CircularPad"		"off"
EndSection
```

---

