---
title: "Touchpad EdgeMotion feature missing"
date: 2016-01-04
forum: New to Ubuntu
---

### Post by louise3 on 2016-01-04
I am using Ubuntu 14.04 on a HP 350 G1 laptop (dual boot with Win7). In Win7 there is edge motion functionality on my touchpad (when dragging an object and reaching the edge of the touchpad, the motion does not stop there, but continues to move). In Ubuntu, I cannot see that this feature is available. Could there be a way to find/enable this feature?

Output from tpconfig:
```
$ sudo tpconfig -i
    Found Synaptics Touchpad.
    Firmware: 8.96 (multiple-byte mode).
    Sensor type: unknown (0).
    Geometry: rectangular/landscape/up.
    Packets: absolute, 80 packets per second.
    Corner taps disabled;        no tap gestures.
    Edge motion: none.
    Z threshold: 6 of 7.
    2 button mode; corner tap is right button click.
```

Output from xinput:
```
$ xinput list-props "SynPS/2 Synaptics TouchPad"
Device 'SynPS/2 Synaptics TouchPad':
    Device Enabled (139):    1
    Coordinate Transformation Matrix (141):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (263):    1
    Device Accel Constant Deceleration (264):    2.500000
    Device Accel Adaptive Deceleration (265):    1.000000
    Device Accel Velocity Scaling (266):    12.500000
    Synaptics Edges (267):    1534, 5402, 1259, 4613
    Synaptics Finger (268):    25, 30, 0
    Synaptics Tap Time (269):    180
    Synaptics Tap Move (270):    261
    Synaptics Tap Durations (271):    180, 180, 100
    Synaptics ClickPad (272):    0
    Synaptics Middle Button Timeout (273):    75
    Synaptics Two-Finger Pressure (274):    282
    Synaptics Two-Finger Width (275):    7
    Synaptics Scrolling Distance (276):    119, 119
    Synaptics Edge Scrolling (277):    1, 1, 0
    Synaptics Two-Finger Scrolling (278):    0, 0
    Synaptics Move Speed (279):    1.000000, 1.750000, 0.033608, 0.000000
    Synaptics Off (280):    2
    Synaptics Locked Drags (281):    0
    Synaptics Locked Drags Timeout (282):    5000
    Synaptics Tap Action (283):    2, 3, 0, 0, 1, 3, 0
    Synaptics Click Action (284):    1, 1, 0
    Synaptics Circular Scrolling (285):    0
    Synaptics Circular Scrolling Distance (286):    0.100000
    Synaptics Circular Scrolling Trigger (287):    0
    Synaptics Circular Pad (288):    0
    Synaptics Palm Detection (289):    0
    Synaptics Palm Dimensions (290):    10, 200
    Synaptics Coasting Speed (291):    20.000000, 50.000000
    Synaptics Pressure Motion (292):    30, 160
    Synaptics Pressure Motion Factor (293):    1.000000, 1.000000
    Synaptics Resolution Detect (294):    1
    Synaptics Grab Event Device (295):    0
    Synaptics Gestures (296):    1
    Synaptics Capabilities (297):    1, 0, 1, 1, 1, 1, 1
    Synaptics Pad Resolution (298):    80, 46
    Synaptics Area (299):    0, 0, 0, 0
    Synaptics Noise Cancellation (300):    8, 8
    Device Product ID (258):    2, 7
    Device Node (259):    "/dev/input/event4
```

I have seen in other posts, e.g. this one:
[http://ubuntuforums.org/archive/index.php/t-2176231.html](http://ubuntuforums.org/archive/index.php/t-2176231.html)
that other users have also these properties```

Synaptics Edge Motion Pressure (281): 30, 160
Synaptics Edge Motion Speed (282): 1, 929
Synaptics Edge Motion Always (283): 0
```

---

### Post by DuckHook on 2016-01-04
Hi louise3 and welcome to Ubuntu and the forums.

There is a simple little graphical utility called "Pointing devices" that may help. Please do:```
sudo apt-get update && sudo apt-get install gpointing-device-settings
```...and you should be able to see the utility on your dash after installation. It is best to copy and paste my command into the terminal rather than retyping because Linux is both case-sensitive and very persnickety about proper spelling, etc.

---

### Post by louise3 on 2016-01-05
Thanks DuckHook
Its a nice GUI, but as far as I can see it does not give me any additional features. I am still missing the EdgeMotion feature.

---

### Post by DuckHook on 2016-01-05
I do not use *xinput*, so this will be a case of being led by the blind. Be forewarned that I don't pretend to know what I'm doing here. You may wish to delay this implementation until you've heard from more knowledgeable people on this forum. However, based on the syntax of the example you cite and taking a few guesses on the structure, you might try:```
xinput set-prop "SynPS/2 Synaptics TouchPad" "Synaptics Edge Motion Pressure" 30, 160
``````
xinput set-prop "SynPS/2 Synaptics TouchPad" "Synaptics Edge Motion Speed" 1, 929
``````
xinput set-prop "SynPS/2 Synaptics TouchPad" "Synaptics Edge Motion Always" 0
```Copy and paste instead of retyping, so as not to confuse (Letter) O and (number) 0, for example. You may have to change the value in the last command to 1 but try it with 0 first. You will have to reboot (or at least logout-login) to reload X before it will work&#8213;if it even works. Again, a word to the wise, I am only going by a semi-educated guess based on the info that you've dug up, so there is a small possibility that my ignorance will gum up your system.

---

### Post by louise3 on 2016-01-05
Yes, I believe this would be a way to set these properties if they did exist. Running these commands only gives me the information that they do not exist:
```
$ xinput set-prop "SynPS/2 Synaptics TouchPad" "Synaptics Edge Motion Always" 0
property 'Synaptics Edge Motion Always' doesn't exist, you need to specify its type and format
```
unfortunately

---

### Post by DuckHook on 2016-01-06
I'm exploring xinput as we go along, so let's first do:```
xinput list
```to see which ID has been assigned to your mouse. Please post back results.

---

### Post by louise3 on 2016-01-06
My touchpad has id 11, it seems:
```
$ xinput list
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=11    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Power Button                                id=8    [slave  keyboard (3)]
    &#8627; HP Truevision HD                            id=9    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=10    [slave  keyboard (3)]
    &#8627; HP WMI hotkeys                              id=12    [slave  keyboard (3)]
    &#8627; HP Wireless hotkeys                         id=13    [slave  keyboard (3)]

```

---

### Post by DuckHook on 2016-01-06
I really must thank you for introducing me to a new tool that I can now add to my geeky toolbox. I did not know of the existence of xinput until you introduced me to it. I know that this doesn't help your situation any, but it at least gives the both of us some new tools to use.

You have already produced the xinput list of properties for your touchpad and it does not contain the "Edge Motion" properties. Neither does mine. I suspect that this is due to some combination of HW/Driver limitation in our machines. In my case, I don't really miss this feature that much because I hold down the physical button if I want to drag (I find that I can be so much more precise that way), but I can see why enabling the feature is useful.

Problem is, through numerous searches, I haven't discovered how this feature can be added. My suspicion is that it isn't possible without some sort of software hack, which I am not capable of doing. However, I do notice that your xinput properties include the option of lock-dragging. I have no idea how to do this, but [this]("http://ubuntuforums.org/showthread.php?t=2059768&p=12254545#post12254545") link points to another poster who was able to activate his and felt that it worked as an acceptable substitute. In his case, he actually did have Edge Motion, which he ultimately enabled. It seems that this option is simply not available to you and me.

Give the "Lock Drag" property a try. Instructions are in the provided link. I may try it as well, now that I'm curious about it.

I will continue to explore this topic now that I've been introduced to it. If I come across anything of further interest, I will post back to this thread.

---

### Post by DuckHook on 2016-01-06
I doubt that this will help any further, but a similar tool to *xinput* is *synclient*. Just type *synclient* in a terminal and it will give you a list of all properties that your driver/touchpad supports. In my case, although the terminology is a bit different, I saw nothing that could be activated to enable edge motion. This is not surprising since both apps probably access the same driver options, and Edge Motion probably isn't offered by our particular drivers. I have since looked up the *xinput* properties of another old laptop I have and same thing: no Edge Motion.

This is starting to feel like beating a dead horse.

---

