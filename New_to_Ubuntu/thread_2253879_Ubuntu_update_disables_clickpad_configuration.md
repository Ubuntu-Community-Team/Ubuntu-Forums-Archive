---
title: "Ubuntu update disables clickpad configuration"
date: 2014-11-23
forum: New to Ubuntu
---

### Post by Hellboy256 on 2014-11-23
[TABLE]
[TR]
[TD="class: postcell"]                Since Ubuntu doesn't interpret my clickpad and trackpoint on my lenovo e540 properly I found this script [http://pastebin.com/hsSUWa3a](http://pastebin.com/hsSUWa3a) online that solves everything. It creates all necessary files in /etc/X11/xorg.conf.d including 
90-evdev-trackpoint.conf.  But everytime I run an update on Ubuntu (doesn't seem to matter what  the update contains, because once only Chrome was updated and it still  happened) the scroll function on my clickpad doesn't work anymore. All files are still unchained  in the mentioned directory... I currently solve the problem by deleting all files from /etc/X11/xorg.conf.d/ and run the script again...

  Does anyone know what disables my configuration?
  This is the 90-evdev-trackpoint.conf file:

```


 Section "InputClass"
    Identifier "Clickpad"
    MatchIsTouchpad "on"
    MatchDevicePath "/dev/input/event*"
    Driver "evdev"
    # Synaptics options come here.
Option "TapButton1" "1"
Option "TapButton2" "3"
Option "TapButton3" "2"
Option "SoftButtonAreas" "60% 0 0 40% 40% 60% 0 40%"
    Option "AreaTopEdge"          "40%"
    Option "AreaBottomEdge"       "0"
EndSection

Section "InputClass"
Identifier   "TrackPoint"
MatchProduct "TrackPoint"
MatchDriver  "evdev"
Option       "EmulateWheel"       "1"
Option       "EmulateWheelButton" "2"
Option       "XAxisMapping"       "6 7"
EndSection

```


[/TD]
[/TR]
[/TABLE]

---

### Post by d4m1r on 2014-11-24
Are you sure all that you installed was a Chrome update? I don't see how that could have triggered your X11 settings to reset...

---

### Post by Hellboy256 on 2014-11-25
Yes I am sure about that. 
And it happens every time i perform an update now, I didn't check every update I execute but I don't think there is an update of X11 every time?

---

### Post by Hellboy256 on 2014-12-04
Has nobody any idea what might cause this issue??

---

