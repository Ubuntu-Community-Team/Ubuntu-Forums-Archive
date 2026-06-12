---
title: "installation issue- no screens found"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by mortonman on 2008-04-28
I am completely new to linux and pretty green around computers.

I tried to install ubuntu using WUBI 8.04 All seemed well until i got a 
**fatal server error: no screens found**

I have tried starting in safe graphic mode but I still get the same message.

I am installing on an acer aspire 1350 laptop

specs

Mobile amd xp 2600+
display adapter- via/s3g KM400/KN400

Any help woud be greatly appreciated. This is my first foray out of windows and it isn't a good start!!
 

I opened up the xorg.conf file and took some pictures attached
[IMG]http://farm3.static.flickr.com/2377/2445447486_3c41d92188.jpg?v=0[/IMG]
[IMG]http://farm3.static.flickr.com/2045/2444619493_31b8a7d588.jpg?v=0[/IMG]
[IMG]http://farm3.static.flickr.com/2243/2445444596_f65ecc8221.jpg?v=0[/IMG]

---

### Post by martrn on 2008-04-28
Your /etc/X11/xorg.conf file should contains a screen section something like:

==================================

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation [OR YOUR CARD]"
    Monitor        "YOUR MONITOR MODEL"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1280x960" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

================================

The important bit here being the modes section including         Modes      "1280x960" "1024x768" "800x600" "640x480" and other sections of your xorg.conf file must be set correctly.

try :
type at a terminal :
```
dpkg-reconfigure xserver-xorg
```
to configure your X11 and make sure you select the correct modes that your monitor can / is capebel of displaying.

---

### Post by mortonman on 2008-04-28
> **martrn said:**
> Your /etc/X11/xorg.conf file should contains a screen section something like:



My xorg.conf file is posted above in the picutres. The screen section just says
Section "Screen"
    identifier    "Default screen"
    monitor       "configured monitor"
    device        "configured video device"

---

### Post by martrn on 2008-04-29
> **mortonman said:**
> My xorg.conf file is posted above in the picutres. The screen section just says
Section "Screen"
    identifier    "Default screen"
    monitor       "configured monitor"
    device        "configured video device"

That probebly isn't good enough for x to start. You will need a section that tells xorg the modes your monitor is capable of displaying.

try :
type at a terminal :

```
dpkg-reconfigure xserver-xorg
```

to configure your X11 and make sure you select the correct modes that your monitor can / is capebel of displaying. Pay particualr attention to your monitor section, enter the correct values and this should configure your etc/X11/xorg.conf  file

---

