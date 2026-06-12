---
title: "Only some Options gets applied from /etc/X11/xorg.conf.d folder"
date: 2018-09-19
forum: New to Ubuntu
---

### Post by boqsc on 2018-09-19
```


Section "InputClass"
            Identifier "libinput touchpad disable-horiz-scrolling"
            MatchIsTouchpad "on"
            MatchDevicePath "/dev/input/event*"
            MatchDriver "libinput"
            # here add your option
            Option "HorizontalScrolling" "0"
        Option "AccelerationNumerator" "6"
        Option "AccelerationDenominator" "1"
        Option "AccelerationThreshold" "4"
            Option "AccelSpeed" "-0.5"
EndSection


```

On boot up, only HorizontalScrolling is getting set to 0. 
All other options are not set as if xorg.conf.d didn't contain Options.

My guess is that maybe they are overwritten by something from other Ubuntu software.
I'm using Ubuntu 18.04

What you think about that, how could I regulate for example AccelSpeed in a correct, as intended, non-hacky way?

---

### Post by boqsc on 2018-09-19
Probably overwritten by gnome-control-center, mouse speed can be adjusted using gsettings.
Unsure how gnome-control-center does it. But there might be some clues in their gitlab repository: [https://gitlab.gnome.org/GNOME/gnome-control-center](https://gitlab.gnome.org/GNOME/gnome-control-center)

---

### Post by mc4man on 2018-09-21
Maybe try moving Option "AccelSpeed" "-0.5"  above the 3 options currently above it as it 'appears' those other 3 are not valid options.
Refer to man libinput or online - 
[http://manpages.ubuntu.com/manpages/bionic/man4/libinput.4.html](http://manpages.ubuntu.com/manpages/bionic/man4/libinput.4.html)

---

