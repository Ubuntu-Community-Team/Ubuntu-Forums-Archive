---
title: "Missing monitor resolution"
date: 2017-04-12
forum: New to Ubuntu
---

### Post by aurinko2 on 2017-04-12
Ok, so I've had this problem for ages, and it always resurfaces when I upgrade distribution. Some years I manage to get it working, some years I give up and work with bad resolution.

So I upgraded to ubuntu 16.10 and now my nvidia control panel doesn't have the correct resolution listed at all. xrandr --addmode fails, and based on my googling it's because it doesn't accept the resolution 1600x1200_85.00, which works just fine in Windows (blech). Now my monitor is a 20-year-old CRT, which I believe doesn't give good EDID and I'm guessing this is the problem.

**get-edid** gives me this:
```
This is read-edid version 3.0.2. Prepare for some fun.
Attempting to use i2c interface
No EDID on bus 1
No EDID on bus 2
No EDID on bus 3
1 potential busses found: 0
Bus 0 doesn't really have an EDID...
Couldn't find an accessible EDID on this computer.
Attempting to use the classical VBE interface

    Performing real mode VBE call
    Interrupt 0x10 ax=0x4f00 bx=0x0 cx=0x0
    Function supported
    Call successful

    VBE version 300
    VBE string at 0x11100 "NVIDIA"

VBE/DDC service about to be called
    Report DDC capabilities

    Performing real mode VBE call
    Interrupt 0x10 ax=0x4f15 bx=0x0 cx=0x0
    Function supported
    Call successful

    Monitor and video card combination does not support DDC1 transfers
    Monitor and video card combination supports DDC2 transfers
    0 seconds per 128 byte EDID block transfer
    Screen is not blanked during DDC transfer

Reading next EDID block

VBE/DDC service about to be called
    Read EDID

    Performing real mode VBE call
    Interrupt 0x10 ax=0x4f15 bx=0x1 cx=0x0
    Function supported
    Call failed

The EDID data should not be trusted as the VBE call failed
EDID claims 255 more blocks left
EDID blocks left is wrong.
Your EDID is probably invalid.
&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;Looks like VBE was successful. Have a good day.

```

I don't really understand the output of get-edid.

I have dug out the manuals for my CRT, and its frequencies are: fH: 30-127 kHz, fV: 50-180 Hz, as some website said that I need to put these in xorg.conf.

**My questions are: How do I do that? Am I at all on the right track here? Many websites say that xorg.conf is no longer used... if that's true, then what should I do?**

Thanks for all your help!

---

### Post by Autodave on 2017-04-12
First off, did you install any Nvidia drivers and where did you get them from?  Secondly, is the monitor hooked up by a VGA cable?

Can you identify the Nvidia card in your machine and what driver, if any, you installed?

Generally, when I see that error, the first thing I want to do (assuming you are using a VGA cable) is to try a known good cable. A failed cable or a cheap cable will not report the monitor properly to the video card.

---

