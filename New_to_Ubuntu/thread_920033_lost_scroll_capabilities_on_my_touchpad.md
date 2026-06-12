---
title: "lost scroll capabilities on my touchpad"
date: 2008-09-14
forum: New to Ubuntu
---

### Post by adamogardner on 2008-09-14
yes I just fixed screwed up graphics and now everything is great but I can't scroll.  What do I have to do now?

---

### Post by k33bz on 2008-09-14
First off, did you try to enable your scroll pad.

Im assuming your on a latop

---

### Post by adamogardner on 2008-09-15
> **k33bz said:**
> First off, did you try to enable your scroll pad.

Im assuming your on a latop

I'm on a laptop.  I enabled nothing but my graphics which were screwed up.  ny cursor moves fine, i just can't scroll the page. like now when I want to submit, I have to use the scroll bar or down arrows - LAME!

---

### Post by k33bz on 2008-09-15
ok, you need to enable your touch pad. it is usually Fn+????? Each laptop is different. You may have accidentally turned your touchpad off when you were trying to fix the graphix on your laptop. 

My Laptop is an Acer Aspire 3680 my touchpad control is Fn+F7

---

### Post by adamogardner on 2008-09-15
> **k33bz said:**
> ok, you need to enable your touch pad. it is usually Fn+????? Each laptop is different. You may have accidentally turned your touchpad off when you were trying to fix the graphix on your laptop. 

My Laptop is an Acer Aspire 3680 my touchpad control is Fn+F7

what is "Fn"?

---

### Post by k33bz on 2008-09-15
It is your function key, usually placed on the bottom left hand of your keyboard. between Ctrl (control) and your super button (the button that looks like a window logo) next 2 buttons would be your Alt and space buttons.

---

### Post by adamogardner on 2008-09-15
> **k33bz said:**
> It is your function key, usually placed on the bottom left hand of your keyboard. between Ctrl (control) and your super button (the button that looks like a window logo) next 2 buttons would be your Alt and space buttons.

got it  wow never knew it was there.  I'm trying to reference the correct combination for my system.  I don't care to just start hitting buttons.?

---

### Post by k33bz on 2008-09-15
> **adamogardner said:**
> got it  wow never knew it was there.  I'm trying to reference the correct combination for my system.  I don't care to just start hitting buttons.?
i wouldnt do that, you might push the wrong combo and get some unwanted effects. What type of laptop u have, manufactureer and model, and i will go look it up for you

---

### Post by adamogardner on 2008-09-15
> **k33bz said:**
> i wouldnt do that, you might push the wrong combo and get some unwanted effects. What type of laptop u have, manufactureer and model, and i will go look it up for you

hp pavillion dv6700

---

### Post by k33bz on 2008-09-15
ok, found the manual.

you wont be needing the function key for this. on the top of your touchpad, right next to the ligh (i dont know if the light is working in linux) there is a button, that is the button to toggle your touch pad on and off).

[IMG]http://img.photobucket.com/albums/v471/houstonkeebler/button.jpg[/IMG] it is labeled  on number 4

[the service manaul for your laptop]("static.tigerdirect.com/pdf/HP_Pavilion_dv6500_dv6600_dv6700_NotebookPC-MnSG.pdf") its in PDF form.

btw, did you get the fingerprint scanner working in linux

---

### Post by lswest on 2008-09-15
I doubt that's his problem, since he can use the touchpad to move the cursor.  Check your xorg.conf file to see if there is a driver specified for the touchpad.  If it's there and the device driver is not synaptics, that's your problem.  Otherwise I'm not sure.

---

### Post by adamogardner on 2008-09-15
> **lswest said:**
> I doubt that's his problem, since he can use the touchpad to move the cursor.  Check your xorg.conf file to see if there is a driver specified for the touchpad.  If it's there and the device driver is not synaptics, that's your problem.  Otherwise I'm not sure.

can I have the commands for that specifically?

---

### Post by k33bz on 2008-09-15
> **lswest said:**
> I doubt that's his problem, since he can use the touchpad to move the cursor.  Check your xorg.conf file to see if there is a driver specified for the touchpad.  If it's there and the device driver is not synaptics, that's your problem.  Otherwise I'm not sure.

well I assumed his touchpad wasnt working at all. Figured he might of plugged in a mouse, or used hotkeys to move his cursor around.

---

### Post by lswest on 2008-09-15
> **adamogardner said:**
> can I have the commands for that specifically?

Sure, basically what I do is this:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak ##makes a backup of it
sudo gedit /etc/X11/xorg.conf
```

and the part that corresponds to my touchpad (on an HP dv6545eg) is this:
> Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard" "CoreKeyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "Synaptics Touchpad"
EndSection
##cut out some stuff corresponding to my keyboard and configured mouse
Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizEdgeScroll" "0"
    Option	   "SHMConfig"	"True"
EndSection

you may, however, need to change the device name (not sure how to figure that one out)

Hope it helps,
Lswest

and @ k33bz I can see how you thought that, I guess I understood what he was saying in that way since I had had a similar issue with my own touchpad.

---

### Post by knix on 2008-09-15
Just add this to your mouse/touchpad section in ypur xorg.conf:
```
Option  "HorizEdgeScroll"  "True"
Option  "VertEdgeScroll"  "True"
```

I had to do this in Debian Sid.

---

### Post by adamogardner on 2008-09-15
all I have is this:

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Thu Feb 14 18:20:37 PST 2008

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 110.0
    VertRefresh     50.0 - 150.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

---

### Post by lswest on 2008-09-15
The relevant section is this:
> **adamogardner said:**
> 
Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection
just change the driver to synaptics and add the vertical and horizontal scroll options (however, back up the file before editing it, just in case it doesn't work).

---

### Post by adamogardner on 2008-09-15
> **lswest said:**
> The relevant section is this:

just change the driver to synaptics and add the vertical and horizontal scroll options (however, back up the file before editing it, just in case it doesn't work).

i backed it up as you described in your previous post correct?

---

### Post by k33bz on 2008-09-15
> **adamogardner said:**
> i backed it up as you described in your previous post correct?
 just change this area.
```
Section "InputDevice"
# generated from default
Identifier "Mouse0"
Driver "synaptics"
Option "Protocol" "auto"
Option "Device" "/dev/psaux"
Option "Emulate3Buttons" "no"
Option "ZAxisMapping" "4 5"
EndSection
```


see, change the Driver from "mouse" to "synaptics"

---

### Post by lswest on 2008-09-15
> **adamogardner said:**
> i backed it up as you described in your previous post correct?

Correct, and then editing the parts we listed above should do it.

---

### Post by adamogardner on 2008-09-15
it worked, and I'm now discovering the majik of shell scripts.  is there a list or something of gedit scripts that I can explore and tweek one by one?  I'm trying to get real familiar with my system and without a guide it's slow learning.  Thanks so much for the work yu put into this.

i guess what i mean is this command can be used for what else? 
sudo gedit /etc/X11/xorg.conf
Any file in etc?  I'm trying to understand more than I comprehend about this, I just want the "power" in my brain to make things happen here

---

### Post by lswest on 2008-09-15
Well /etc/sysctl is always something interesting to look at, otherwise just check out your .bashrc file in your home folder.  Should keep you busy for a little while ;)  Most files I find are tied to system tweaking tutorials, so why not have a google for those?  (e.g. speed up ubuntu hardy, etc.)

ah, Gedit is just a text editor, much like nano or vim or notepad (from windows).  The /etc/X11/xorg.conf is just the file.  There are hundreds of config files in your system.  Before playing with any of them though, always back it up, and be careful what you change (keep track of it if you can).

If you're interested, I wrote an [aliasing how-to]("http://lswest-ubuntu.blogspot.com/2008/06/aliasing-how-to.html") once that uses the .bashrc file.  Also, I used nano instead of gedit in it, would give you a bit of a change if you're interested.

---

