---
title: "Gateway M-285E Touchscreen/pen"
date: 2014-06-19
forum: New to Ubuntu
---

### Post by lancekates-0 on 2014-06-19
So, I'm newish to Linux.  I can install Ubuntu and Mint, and can do some basic troubleshooting, but still very much a newbie.

I have a Gateway M-285E laptop, which has a Fujitsu Finepoint Digitizer touchscreen and stylus pen.  These worked under Windows XP (which is what the laptop had when I first got it).  I installed Ubuntu 14.04.  Everything seems to work, except the touchscreen and stylus, and the screen doesn't rotate when I put it in 'tablet mode' (and the 4 buttons and the directional pad on the tablet do nothing)

I have done quite a bit of searching and found that I needed some fpit driver. When I try to install the .deb, I get an error that says it 'breaks' some dependent file, and then it won't install.

I've found other help, including step by step directions to edit files (xorg.conf, and a few others) and adding some setserial stuff. I went through all of that step by step.. still won't work.

I've put about 5 hours total into this one issue.  Help?

it looks like linux still doesn't recognize that i even have a touchscreen.....From "xinput list":

```
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=11    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=10    [slave  keyboard (3)]


```

---

### Post by lancekates-0 on 2014-06-24
Here is where I am at now.  I have followed the directions [here]("http://ubuntuforums.org/showthread.php?t=1365055") but the dmesg line provided no output for me.
I also tried [these steps]("http://ubuntuforums.org/showthread.php?t=1064838") and even this [tutorial]("https://help.ubuntu.com/community/FujitsuStylus")

The end result is that my system now won't boot.  heh.  I'm running off a liveCD now, about to wipe and reinstall 14.04.

before I do, here is my xorg.conf file:
```
Section "InputDevice"
        Identifier "Tablet"
        Driver "fpit"
        Option "Device" "/dev/ttyS0"
        Option "AlwaysCore" "on"
        Option "InvertY"
        Option "MaximumXPosition" "12550"
        Option "MaximumYPosition" "7650"
        Option "MinimumXPosition" "400"
        Option "MinimumYPosition" "400"
        Option "Passive" "false"
        Option "SendCoreEvents"
EndSection

Section "ServerLayout"
        InputDevice     "Tablet"
EndSection
```

and here is my serial.conf:
```
/dev/ttyS0 uart 16550A port 0x06a8 irq 4 baud_base 38400 spd_normal skip_test
```

I have tried to install this fpit driver I keep seeing referenced, and that may be the part I am missing, but I just can't figure out how to do it.  And while every site that references the driver says to "install it" none say how.  I've tried the "sudo apt-get install" and no go.

help?

---

