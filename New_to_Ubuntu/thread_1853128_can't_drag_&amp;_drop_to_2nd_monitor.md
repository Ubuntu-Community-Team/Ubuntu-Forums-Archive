---
title: "can't drag &amp; drop to 2nd monitor"
date: 2011-10-01
forum: New to Ubuntu
---

### Post by 02darkRS on 2011-10-01
I have been working & searching for over three hrs. Why can't I drag & drop from my monitor 1 to monitor 2? 
I have literally tried every single possible command or nvidia setting found via google searching. aside from finally getting monitor 2 to even display the desktop..... it has been fruitless. there seems to be endless supplies of variations on what to do. I thought I had found the answer when one person clearly stated Xinerama was what allowed windows like 2nd monitor actions..... all that netted me was the old monitor showing the incorrect resolution & not allowing me to do anything except cold restart into safe mode & reboot to old graphics settings. /rant

**Does anyone actually know why I can't drag to the 2nd window & a definitive explanation of how to enable this feature? **

---

### Post by Paddy Landau on 2011-10-01
Silly question, but... Does your software know which monitor is to the left? Have you tried dragging both left and right -- and indeed down or up? You may need to change the relative positions in the monitor settings.

---

### Post by 02darkRS on 2011-10-01
yes, everything is set up in the correct orientation. there's plenty of complaints of the same issue found via search but there does not seem to be a real answer anywhere.

---

### Post by Krytarik on 2011-10-01
It seems like you've set up your monitors as separate X screens. If that's the case, I'm pretty sure that you can forget about the idea of moving windows between them.

Btw., you left this [thread]("http://ubuntuforums.org/showthread.php?t=1849137") hanging.

Greetings.

---

### Post by 02darkRS on 2011-10-01
I didn't try to set them up that way. Where would I have inadvertently set them up that way without ever choosing set up as separate screens? and why would this option even exist since, if i am running something on screen 0. screen 1 states another instance of this program is open. you must close it first........ if it allowed me to open something on the "seperate" screenm then i could work around but all i have now is a pretty picture........  

The way you make it sound it's like I chose a setting that can never be changed?????? If that's the case then what kind of person is this OS made for? None of you ever need different set ups after installing things? That just sounds ludicrous..... there's no way I can start over with my screen set up? 

and other thread marked solved. thanks for the heads up.

edit: if this is the case please tell me how I should have set them up. since, so far my set up isn't working for anything I've tried to do..... i'll start fresh with the partitions being mounted & two screens as not separate. then write a tut that doesn't assume the next noob knows 1,000 things about switching from windows when I write it.  all i wanted was an sdd with the OS & a HDD with the data files. That didn't work even though I followed the only directions given. Now, all I did was follow setting up dual screen directions & of course they don't work either. I'd like to be part of this free movement but man it's getting to be not worth my time. I could have bought windows with the amount of time I have spent getting nowhere here.

---

### Post by Krytarik on 2011-10-01
Hey, just work on improving the Xinerama setup (or also TwinView if you have an Nvidia card, and are using the proprietary driver), as that's the only way to go, if you want to be able to move windows between your both monitors.

Also, how did you set up your current configuration in the first place, namely "/etc/X11/xorg.conf"?

---

### Post by 02darkRS on 2011-10-01
it wouldn't let me set anything up for an hour. finally i found a thread saying to open the preview when it blocks the save of the config. copy it, then save it overwriting the current config file. after that worked i was able to get the second monitor running by restarting X.
">[[IMG]http://farm7.static.flickr.com/6173/6201995059_4dbc51f642.jpg[/IMG]]("http://www.flickr.com/photos/65174795@N02/6201995059/")

[[IMG]http://farm7.static.flickr.com/6179/6201995055_d37713ba2a.jpg[/IMG]]("http://ubuntuforums.org/%3Ca%20href=")">

[[IMG]http://farm7.static.flickr.com/6144/6202524304_8004da5e96.jpg[/IMG]]("http://ubuntuforums.org/%3Ca%20href=")">

While taking the screenshots I see the seperate X screens but that was the default. I tried changing it to twinview which did not fix the problem. 

> Hey, just work on improving the Xinerama setup (or also TwinView if you  have an Nvidia card, and are using the proprietary driver), as that's  the only way to go, if you want to be able to move windows between your  both monitors.^^^ could you be any more cryptic? seriously, I did work on the settings. I tried every suggestion I could find for 3 hrs. Do you know specifically how to fix this or not?

---

### Post by 02darkRS on 2011-10-01
Solved: Choose  Twin View. Ignore the meta errors that pop up. Save your config. Restart X. If you need a step by step walk through to actually get you through this pm me if you get no response here. being a noob, i'll treat you like one too & not assume you know to ignore a big noise & red pop up telling you there are errors with your last setting.................... I remembmer now that's why I never went any further with the twinview. it always throws a meta error. for giggles I went ahed & ignored it, & now it works. :P:confused::(:popcorn::lolflag:  = how ubuntu is making me feel  

i really want to learn this stuff but I don't have this kind of time.

---

### Post by ttr398 on 2011-10-01
Hi there

Think my problem is identical to OP.

I've tried under unity and classic. Managed to get xorg.conf to the point where it shows similar desktops on both screens, I think separate x screens, without xinerama.

If I try to set up xinerama, it does precisely nothing (through the settings UI or by editing xorg.conf) at all. 

If I set up twinview (my ideal scenario - had this working under intrepid absolutely fine!), the display goes absolutely crazy - left, smaller monitor appears to be displaying correctly, right, larger and primary screen displays utterly incorrectly. Seems to extend the desktop by about 500~ pixels or more off the edge of the screen (left edge). When moving the cursor across there's a definite period where it is nowhere!

Orientation is set correctly. Nvidia-settings shows both screens of course, but xrandr and ubuntu's monitors window doesn't.

Ideally I just want to set up an extended single desktop across the two screens, same as the OP I think!

Tried a lot of fettling, not had any usable results!


I'm running a 22" monitor, 1600x1024, and a 24" at 1920x1080. The card is an NVidia 8800 GTS, with two DVI outputs. 

Here's my xorg.conf:

```

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 270.29  (buildd@allspice)  Fri Feb 25 14:42:07 UTC 2011

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 270.41.06  (buildmeister@swio-display-x86-rhel47-08.nvidia.com)  Mon Apr 18 15:14:00 PDT 2011

Section "ServerLayout"
# Removed Option "Xinerama" "0"
    Identifier     "Layout0"
    Screen      0  "Screen0" LeftOf "Screen1"
    Screen      1  "Screen1" 1600 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "1"
EndSection

Section "Files"
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
    ModelName      "Chi Mei Optoelectronics corp. CMC 22 W"
    HorizSync       30.0 - 82.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 81.0
    VertRefresh     56.0 - 60.0
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GTS"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GTS"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"

# Removed Option "metamodes" "DFP-0: nvidia-auto-select +0+0"
# Removed Option "TwinView" "1"
# Removed Option "metamodes" "DFP-0: 1600x1024 +0+0, DFP-1: 1920x1080 +1600+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinViewXineramaInfoOrder" "DFP-1"
    Option         "TwinView" "0"
    Option         "metamodes" "DFP-0: 1600x1024 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"

# Removed Option "TwinView" "1"
# Removed Option "metamodes" "DFP-1: nvidia-auto-select +0+0"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "TwinViewXineramaInfoOrder" "DFP-1"
    Option         "metamodes" "DFP-1: 1920x1080 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection


```

I'm really hoping I don't have to go back to Windows, I miss using Ubuntu and this release looks pretty flash!

---

### Post by Krytarik on 2011-10-01
> **02darkRS said:**
> :P:confused::(:popcorn::lolflag:  = how ubuntu is making me feel  

i really want to learn this stuff but I don't have this kind of time.
Really, it's the same for most of us, actually you forgot the most annoying one: ](*,)
But most of us like working on technical challenges ... and overcoming them, to get :D .

Greetings.

---

### Post by ttr398 on 2011-10-01
Does this thread being marked as solved mean I should start a separate thread for my issue? The OP's fix does not work for mine, as TwinView doesn't produce error messages, just very weird display problems!

---

### Post by Krytarik on 2011-10-01
> **ttr398 said:**
> Does this thread being marked as solved mean I should start a separate thread for my issue? The OP's fix does not work for mine, as TwinView doesn't produce error messages, just very weird display problems!
Yep, I do recommend so, with a more specific title, pointing to having issues with TwinView.

But two things I want to point out right here:

[LIST]
[*]xrandr, and therefore Ubuntu's built-in "Monitors" tool, doesn't work too great with the proprietary Nvidia driver.
[*]You can definitely only set up the video configuration with "NVIDIA X Server Settings".
[/LIST]

---

### Post by ttr398 on 2011-10-02
Hi

That is largely what I assumed, but I thought it might be relevant that they only see one monitor!

Cheers & kind regards 

Thomas

---

### Post by 02darkRS on 2011-10-02
> **ttr398 said:**
> Hi there

Think my problem is identical to OP.

I've tried under unity and classic. Managed to get xorg.conf to the point where it shows similar desktops on both screens, I think separate x screens, without xinerama.

If I try to set up xinerama, it does precisely nothing (through the settings UI or by editing xorg.conf) at all. 

If I set up twinview (my ideal scenario - had this working under intrepid absolutely fine!), the display goes absolutely crazy - left, smaller monitor appears to be displaying correctly, right, larger and primary screen displays utterly incorrectly. Seems to extend the desktop by about 500~ pixels or more off the edge of the screen (left edge). When moving the cursor across there's a definite period where it is nowhere!

Orientation is set correctly. Nvidia-settings shows both screens of course, but xrandr and ubuntu's monitors window doesn't.

Ideally I just want to set up an extended single desktop across the two screens, same as the OP I think!

Tried a lot of fettling, not had any usable results!


I'm running a 22" monitor, 1600x1024, and a 24" at 1920x1080. The card is an NVidia 8800 GTS, with two DVI outputs. 

I'm really hoping I don't have to go back to Windows, I miss using Ubuntu and this release looks pretty flash!

In all my searching I read a couple of threads regarding that card & it being the problem. Search for that. 

Also, don't worry about Ubuntu's monitor screen. Mine screens finally work yet, that window is still wrong. It can't even correctly identify my 0 screen. So, ease some of your concern & just forget that window. 

You did not mention this but it seems like you must be doing it: are you restarting X? (Ctrl+Alt+Backspace) enable by going to: System>Preferences>Keyboard>LayoutsTab>Options>Click Key Sequence to Kill the X Server > tick the radio box. 
Redo your settings, Save Config, Kill the X server. 
This was the initial problem I had once I finally was able to save my config file. 

If you are restarting X. Here is what finally worked for me: 
Choose: TwinView (No Xincinerama) that incinerated my system & caused a safe boot to repair back to stock settings. 
Do tick the make primary display radio box on Monitor 0. Position it as absolute. 
My second monitor keeps reverting to absolute but the first time I got mine to work I set it for "Right of":
Save Config
Restart X. 

Try rebooting as well. I had to fully reboot during a couple setting errors for things to work. My twinview also caused wacky responses the first 100 times....... 

In Nvidia X Server Settings Window-
[[IMG]http://farm7.static.flickr.com/6152/6204664092_e1d007f6de.jpg[/IMG]]("http://ubuntuforums.org/%3Ca%20href=")


[[IMG]http://farm7.static.flickr.com/6169/6204664110_acbbc751b4.jpg[/IMG]]("http://ubuntuforums.org/%3Ca%20href=")

[[IMG]http://farm7.static.flickr.com/6179/6204664124_f1f3d65858.jpg[/IMG]]("http://ubuntuforums.org/%3Ca%20href=")

[[IMG]http://farm7.static.flickr.com/6168/6204664138_62b3c21bbb.jpg[/IMG]]("http://ubuntuforums.org/%3Ca%20href=")


I apparently need to learn  how to screen shot now with two monitors. sorry

---

### Post by 02darkRS on 2011-10-02
> **ttr398 said:**
> Does this thread being marked as solved mean I should start a separate thread for my issue? The OP's fix does not work for mine, as TwinView doesn't produce error messages, just very weird display problems!

As I said above, I read a lot of complaints with users of your card. That might be your problem.... or it could just be you have something set wrong. Did you try setting It as above? Do twin view after you've unticked Xcinerama.

---

