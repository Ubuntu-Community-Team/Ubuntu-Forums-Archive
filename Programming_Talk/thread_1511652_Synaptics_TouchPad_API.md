---
title: "Synaptics TouchPad API?"
date: 2010-06-17
forum: Programming Talk
---

### Post by PaulW89 on 2010-06-17
Hello everyone.

I want to use my touch pad (Lenovo Thinkpad T400) to draw little images and write down short notes.

To do so, I have to read out the touch pads absolute X and Y values.
Now my question: Is there an API for the Synaptics touch pad I can access through C?
If not, I'm also not afraid to read in the raw data coming from the touchpad myself. I already have the document describing the packet structure.

Doing a ```
sudo cat /dev/input/mouse1
``` outputs the raw data coming from my external USB mouse (but only when I move my mouse or click a button...shouldn't there be a constant data stream?). I also tried all other devices but couldn't find my touch pad in the /dev/ folder.

I hope anybody can help me. :-)

Here is some additional info on my touch pad:
```
I: Bus=0011 Vendor=0002 Product=0007 Version=01b1
N: Name="SynPS/2 Synaptics TouchPad"
P: Phys=isa0060/serio1/input0
S: Sysfs=/devices/platform/i8042/serio1/input/input9
U: Uniq=
H: Handlers=mouse2 event9 
B: EV=b
B: KEY=420 0 70000 0 0 0 0 0 0 0 0
B: ABS=11000003

```

I am using Ubuntu 10.04. I haven't modified anything regarding input device configuration/xorg.conf etc. so far.

Greetings from Germany,
Paul

---

### Post by nvteighen on 2010-06-17
Have you considered to do this using the X Window System API rather than directly interfacing the touchpad? I guess it could be easier.

---

### Post by PaulW89 on 2010-06-17
Thanks for your answer! But is that even possible since I need to read out the absolute X,Y coordinates on the touch pad? Of course, if I just needed the coordinates of the mouse cursor on the screen, I would use the X API.
If it really IS possible, would you be kind enough to give me a hint on which functions to use?

Have a nice day,
Paul

---

### Post by nvteighen on 2010-06-17
> **PaulW89 said:**
> Thanks for your answer! But is that even possible since I need to read out the absolute X,Y coordinates on the touch pad? Of course, if I just needed the coordinates of the mouse cursor on the screen, I would use the X API.
If it really IS possible, would you be kind enough to give me a hint on which functions to use?

Have a nice day,
Paul

No, I really don't know about this and was a bit thinking aloud :P From what I know X is behind all that stuff, not the kernel.

But, I see there's something called the General Purpose Mouse interface ([http://unix.schottelius.org/gpm/](http://unix.schottelius.org/gpm/)) (gpm in the Debian's repos, so I guess it's the same in Ubuntu's). But, it also seems from my research that the usual way to do this is by using /dev/input/mouse<number>

EDIT: Wait a moment, have you tried installing xerver-xorg-input-synaptics-dev?

---

### Post by wildwood on 2012-04-05
Hi, All.

 I too am looking for a way to access the mousepad inpuit in raw form, to change MIDI-control-like data in a sequencer, though I am looking for full XYZ data not just XY. I presumed this was possible when thinking about how the synaptics driver in windows displays a pressure sense green blob icon the task tray. I've been pouring through the X documentation I can find and come a blank so far.

How does the input system detect two-finger scroll? or side-scroll? does the touchpad electronics deal with it all and just send mouse-like data?

I too tried to sudo cat the relevant file in /dev/input and also got nothing coming out. I presume that the touchpad is somehow dealt with differently to a standard mouse.

did you get anywhere with this in the last 2 years, Paul?

I'm looking to do this in C++ if its relevant at all.

greetings from Italy, BTW

---

### Post by wildwood on 2012-04-05
A few more hours have revealed some more.. if one downloads the source code for the synaptics driver there is in the tools folder a little app (synclient.c) that reads out all the current data you can get for the touchpad via the X server, including x, y, z, and a whole lot more it seems.

---

