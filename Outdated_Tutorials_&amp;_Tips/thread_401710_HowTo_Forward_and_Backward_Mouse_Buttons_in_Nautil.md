---
title: "HowTo: Forward and Backward Mouse Buttons in Nautilus (Easy way)"
date: 2007-04-04
forum: Outdated Tutorials &amp; Tips
---

### Post by majunbu on 2007-04-04
**Introduction**

I will start off this HowTo by stating that there are many other similar howtos but for me they always seemed overly complicated and hard to follow all for the simple task of getting ones forward and backward buttons to function in Nautilus as they already do in a web browser.

**Note:**
This howto article assumes that the reader has a semi understanding of how to edit files and install software in Ubuntu. Also this howto was tested and validated to work with a Logitech MX518 mouse.

**1. Install needed applications**

```
sudo apt-get install xbindkeys xvkbd
```

**2. Edit Xorg.conf**

Make a backup of the xorg.conf file
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

Open the xorg.conf file using whatever text editor you like to use. Here is a sample command that can be used to edit the xorg.conf file.

```
gksu gedit /etc/X11/xorg.conf
```

Look for the "InputDevice" section that deals with the mouse. Edit that section to look something similar to the following.

```

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "Emulate3Buttons" "true"
    Option	   "Buttons" "7"
    Option         "ZAxisMapping" "4 5"
    Option         "ButtonMapping" "1 2 3 6 7"
EndSection

```

Save the changes to the xorg.conf file.

**3. Setup button configuration file**

Edit the following file which is located in the root of your home directory. If the file is not there create the file.

```
gedit .xbindkeysrc
```

Add the following lines to the file exactly as they are shown.

```

"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]"" 
m:0x0 + b:6
 
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]"" 
m:0x0 + b:7

```

**4. Restart X**

At this point you should be able to restart your X session and enjoy your new mouse button functionality.

---

### Post by frodon on 2007-04-06
In many cases only the step2 is needed and in this cases you don't need xbindkeys and xvkbd or any software, you may to have to change *"ButtonMapping" "1 2 3 6 7" *to *"ButtonMapping" "1 2 3 8 9"* in some cases to get it work.

I would advice to try step 2 only and restart X then if it don't work do the other steps.

---

### Post by majunbu on 2007-04-06
> **frodon said:**
> In many cases only the step2 is needed and in this cases you don't need xbindkeys and xvkbd or any software, you may to have to change *"ButtonMapping" "1 2 3 6 7" *to *"ButtonMapping" "1 2 3 8 9"* in some cases to get it work.

I would advice to try step 2 only and restart X then if it don't work do the other steps.

Thanks for the info...I wish I would have known that a few weeks ago. I personally did mess around with the button mappings like you stated and for me I just could not get them working properly (which doesn't mean much as I am still learning Linux). I thought I would try and help contribute something that may make someone elses life a little easier :) 

I guess for me then the next question is if only step two would be needed and it is that easy is it possible to have that functionality implemented by default?

Thanks again for the added info!!

---

### Post by frodon on 2007-04-06
> **majunbu said:**
> I guess for me then the next question is if only step two would be needed and it is that easy is it possible to have that functionality implemented by default?Maybe but unfortunatly this is not true for all the mouses just some of them works when you do only the step 2, that's why for the moment guides like yours are useful ;)

---

### Post by zerwas on 2007-04-06
Wow, thank you.
How did you get the code (m:0x0 + b:6 in your example) for a special button on the mouse?
I have an other mouse and also wanted to do this.

---

### Post by desperado666 on 2007-04-06
start xev in a terminal.

---

### Post by zerwas on 2007-04-06
Thanks desperado666. (Germans everywhere :shock:)
And: Which of these Numbers is the right code? root? state?

The forward and backward buttons give the same code to me :confused:

---

### Post by JLAudioFan on 2007-04-08
Hello!

I did step one and two and this worked like a charm!  Thanks!

Jason

---

### Post by hubris on 2007-06-14
Hi

Let me quick add some comment on this.

i have a Microsoft Intellimouse Explorer 4.0A USB/PS2 compatible mouse. The only thing i did was the following:

```

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "Emulate3Buttons" "true"
    Option	   "Buttons" "7"
    Option         "ZAxisMapping" "4 5"
    Option         "ButtonMapping" "1 2 3 6 7"
EndSection

```

So it seems that only step 2 is needed. Thx for the help majunbu :popcorn:

---

### Post by ashrack on 2007-07-04
This just doesn't work for me. 
I own an MS InteliMouse Optical. 

Here is XORG.CONF
```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
#for IntelliMouse's 7 buttons
	Option          "Buttons"               "7"
	Option		"ButtonMapping"		"1 2 3 6 7"
#a temporary workaround 4 'middle mouse button' scrool feature
#	Option		"EmulateWheel"		"true"
#	Option 		"EmulateWheelButton"	"2"
	Option		"Emulate3Buttons"	"true"
EndSection
```

And the XEV output when I press the 2 sidebuttons:
```
ButtonPress event, serial 29, synthetic NO, window 0x3200001,
    root 0x4d, subw 0x0, time 4032701, (154,22), root:(168,68),
    state 0x10, button 6, same_screen YES

ButtonRelease event, serial 29, synthetic NO, window 0x3200001,
    root 0x4d, subw 0x0, time 4032830, (154,22), root:(168,68),
    state 0x10, button 6, same_screen YES

ButtonPress event, serial 29, synthetic NO, window 0x3200001,
    root 0x4d, subw 0x0, time 4033298, (154,22), root:(168,68),
    state 0x10, button 7, same_screen YES

ButtonRelease event, serial 29, synthetic NO, window 0x3200001,
    root 0x4d, subw 0x0, time 4033398, (154,22), root:(168,68),
    state 0x10, button 7, same_screen YES

```

.xbindkeysrc
```
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[left]"" 
m:0x0 + b:6
 
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[right]"" 
m:0x0 + b:7
```

In firefox BACK and Forth works great but in Nautilus its a no go. Anybody have any other advices?

---

### Post by BLTicklemonster on 2008-07-02
Running Hardy here, have yet to get back buttons working in nautilus. They come out working automatically in firefox, though. Using a Logitech mx 310.

---

### Post by Berrex on 2008-12-10
Sorry to revive an old(ish) thread, but I wanted to share a couple of (basic) pieces of information that I found useful in getting this to work. 

First, I found this page pretty useful:
[http://en.opensuse.org/Logitech](http://en.opensuse.org/Logitech)

Second, in case it's needed, you can enter the following in the terminal to determine what number each of your mouse buttons are:

$ xev

Finally, to get xbindkeys to launch at startup, it's as easy as System > Preferences > Sessions, adding a new item, and having it run the command "xbindkeys" without quotes.

Cheers! Thanks for the guide. Now I can use Opera as my main browser. :)

---

### Post by sproaty on 2008-12-21
I just wanted to post how I got this working on my Razer Diamondback mouse, and other Razer mice, I'm guessing: 

(the settings I post are the different values to the original post)

xorg.conf:
    Option	   "Buttons" "9"
    Option         "ButtonMapping" "1 2 3 8 9"

.xbindkeysrc:
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
m:0x0 + b:8

"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
m:0x0 + b:9


I also added xbindkeys to startup, as the above post says, but I'm not sure whether changing the buttonmappings or adding the startup item fixed it, oh well I'm happy now :)

---

