---
title: "Genius MousePen i608X doesn't work"
date: 2014-04-11
forum: New to Ubuntu
---

### Post by bluesky541 on 2014-04-11
***EDIT:upgraded to 14.10 but still doesn't work...***
Hi, I'm new to Ubuntu and Linux
I tried if my Genius MousePen i608X works, but it just moves like a mouse and doesn't click on anything. I read on an older thread ([http://ubuntuforums.org/showthread.php?t=1899225](http://ubuntuforums.org/showthread.php?t=1899225)) a person had the same problem, but I didn't understand much (about kernels and codes and stuff), so could anyone tell me how to get this tablet to work in a simpler way? :)
here's what it writes for 'lsusb' 
```

Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hubBus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 0a81:0101 Chesen Electronics Corp. Keyboard
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 004: ID 0458:501a KYE Systems Corp. (Mouse Systems) 
Bus 004 Device 002: ID 15ca:00c3 Textech International Ltd. Mini Optical Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```
here's '[COLOR=#000000]xinput --list'
[/COLOR]```
&#9121; Virtual core pointer                        id=2    [master pointer  (3)]&#9116;   &#8627; Virtual core XTEST pointer                  id=4    [slave  pointer  (2)]
&#9116;   &#8627; USB Optical Mouse                           id=9    [slave  pointer  (2)]
&#9116;   &#8627; SynPS/2 Synaptics TouchPad                  id=13    [slave  pointer  (2)]
&#9116;   &#8627; Genius MousePen i608X                       id=15    [slave  pointer  (2)]
&#9123; Virtual core keyboard                       id=3    [master keyboard (2)]
    &#8627; Virtual core XTEST keyboard                 id=5    [slave  keyboard (3)]
    &#8627; Power Button                                id=6    [slave  keyboard (3)]
    &#8627; Video Bus                                   id=7    [slave  keyboard (3)]
    &#8627; Sleep Button                                id=8    [slave  keyboard (3)]
    &#8627; CHESEN USB Keyboard                         id=10    [slave  keyboard (3)]
    &#8627; CHESEN USB Keyboard                         id=11    [slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard                id=12    [slave  keyboard (3)]
    &#8627; HP WMI hotkeys                              id=14    [slave  keyboard (3)]

```[COLOR=#000000]
here's '[/COLOR][COLOR=#000000][FONT=Ubuntu Mono]xinput list-props "Genius MousePen i608X"'[/FONT][/COLOR][COLOR=#000000]
[/COLOR]```
Device 'Genius MousePen i608X':
    Device Enabled (151):    1
    Coordinate Transformation Matrix (153):    1.000000, 0.000000, 0.000000, 0.000000, 1.000000, 0.000000, 0.000000, 0.000000, 1.000000
    Device Accel Profile (276):    0
    Device Accel Constant Deceleration (277):    1.000000
    Device Accel Adaptive Deceleration (278):    1.000000
    Device Accel Velocity Scaling (279):    10.000000
    Device Product ID (271):    1112, 20506
    Device Node (272):    "/dev/input/event10"
    Evdev Axis Inversion (280):    0, 0
    Evdev Axis Calibration (281):    <no items>
    Evdev Axes Swap (282):    0
    Axis Labels (283):    "Abs X" (390), "Abs Y" (391), "Abs Z" (602), "Abs Rotary X" (603), "Abs Rotary Y" (604), "Abs Rotary Z" (605), "Abs Pressure" (392), "None" (0)
    Button Labels (284):    "Button Left" (154), "Button Middle" (155), "Button Right" (156), "Button Wheel Up" (157), "Button Wheel Down" (158), "Button Horiz Wheel Left" (159), "Button Horiz Wheel Right" (160), "Button Side" (599), "Button Extra" (600), "Button Forward" (601), "Button Unknown" (274), "Button Unknown" (274), "Button Unknown" (274), "Button Unknown" (274)
    Evdev Middle Button Emulation (285):    0
    Evdev Middle Button Timeout (286):    50
    Evdev Third Button Emulation (287):    0
    Evdev Third Button Emulation Timeout (288):    1000
    Evdev Third Button Emulation Button (289):    3
    Evdev Third Button Emulation Threshold (290):    20
    Evdev Wheel Emulation (291):    0
    Evdev Wheel Emulation Axes (292):    0, 0, 4, 5
    Evdev Wheel Emulation Inertia (293):    10
    Evdev Wheel Emulation Timeout (294):    200
    Evdev Wheel Emulation Button (295):    4
    Evdev Drag Lock Buttons (296):    0

```[COLOR=#000000]
[/COLOR][COLOR=#000000]my kernel: [/COLOR]3.11.0-19-generic
I have the 32-bit version of ubuntu
please help, I just want to draw.......

---

### Post by fernandojbriquelme on 2014-08-11
I have the same problem, does anybody, know a solution to this one?

---

### Post by vmyska on 2014-09-29
Hi,

I've got the same tablet, still having some issues, but already found a solution for your problem.

From your lsusb:
  [COLOR=#000000][FONT=Ubuntu Mono]Bus 004 Device 004: ID 0458:501a KYE Systems Corp. (Mouse Systems)
[/FONT][/COLOR]
You can see ID 0458:501a. The problem is that you have newer version of MousePen i608X, the old one had ID 0458:05011. Currently the only one solution is to compile a kernel:

1. Download a kernel source (from [www.kernel.org]("http://www.kernel.org")).
2. Make sure that you have enough free space on disk (about 10 GB)
3. Unpack the kernel
4. Modify the ID of MousePen i608X device (on my kernel copy is it file drivers/hid/hid-ids.h, here change 0x5011 to 0x501a)
5. Optionaly make the kernel configuration (you can "copy" current and tweak only new things with command: make oldconfig)
6. Compile the kernel (it will take long long time, command: make)
7. Install modules (command: sudo make module_install)
8. Install the kernel (command: sudo make install)
9. Reboot and select the proper kernel

I hope this will help you, for me it's working.

[B]UPDATE:
[/B]With this modification I couldn't use whole width of tablet (only more than 3/4 worked).
Better than hard modifying product id will be using this patch:
  [http://www.spinics.net/lists/linux-input/msg31764.html](http://www.spinics.net/lists/linux-input/msg31764.html)

There is also updated descriptor with corrected dimensions.

---

### Post by Willi_Meyhoff on 2014-10-08
Sorry to ask, but im a huge newbie, and I really need to get my tablet working.
how do I apply the patch?

---

### Post by gitsythomas on 2014-11-10
Hi, I have the same tablet & same problem.
Filed a  bug. [https://bugs.launchpad.net/ubuntu/+source/unity-control-center/+bug/1391260](https://bugs.launchpad.net/ubuntu/+source/unity-control-center/+bug/1391260)
see this also [http://askubuntu.com/questions/547041/genius-mousepen-i608x-doesnt-work-in-ubuntu](http://askubuntu.com/questions/547041/genius-mousepen-i608x-doesnt-work-in-ubuntu)

---

### Post by ivannanic on 2014-11-18
Hi, I have been experiencing the same problem before, on 14.04 (I can't remember the kernel version I used then), which I managed to solve by remapping the keys of the pen like this:
xinput set-button-mat <device ID> 1 1 1 1 1 1 1 1 3 2 1 1 1 1 
My device ID is 8, yours may vary, check it with xinput --list.
The only thing not working with that fix was pressure, and possibly the mouse you got with the tablet (I lost it so I was unable to check :D).

However, after upgrading to 14.10, the problem turned into an opposite one: the clicks are registered (even the pressure!), although mapping is messed up, but I can't move the pointer with the pen.
My kernel is 3.16.0-24-generic, the latest one supplied by Ubuntu update.
I'll mess around a little more to try to get the mapping right, but as far as moving is concerned, I'm in the total dark.

Thanks in advance.

edit: Now it seems to work as before (and as described in the original post). I can move the pointer and managed to remap the buttons, but I'm not getting pressure now. The only thing I did was install proprietary drivers for graphics card (fglrx-updates).

---

### Post by ivannanic on 2014-11-19
> **gitsythomas said:**
> Hi, I have the same tablet & same problem.
Filed a  bug. [https://bugs.launchpad.net/ubuntu/+source/unity-control-center/+bug/1391260](https://bugs.launchpad.net/ubuntu/+source/unity-control-center/+bug/1391260)
see this also [http://askubuntu.com/questions/547041/genius-mousepen-i608x-doesnt-work-in-ubuntu](http://askubuntu.com/questions/547041/genius-mousepen-i608x-doesnt-work-in-ubuntu)

I have answered that question on Askubuntu, I assume it's yours. See if it might help you.

---

### Post by gitsythomas on 2015-02-04
[COLOR=#333333][FONT=UbuntuRegular]After I upgraded the linux kernel version to 3.18.3-031803-generic, Genius MousePen i608X works well[/FONT][/COLOR]

---

### Post by mörgæs on 2015-02-04
In case people find the thread: The post above means that a 15.04 install should work straight away.

---

### Post by Graeme.N on 2015-06-26
> **mörgæs said:**
> In case people find the thread: The post above means that a 15.04 install should work straight away.

I'm using Xubuntu 15.04 ... the tablet works with the stylus without doing anything other than plugging the tablet into a USB port on my laptop :D .
But ... the mouse isn't working :( .  The tablet acknowledges the mouse, but the computer doesn't.

Actually, given that this thread is marked solved, it would probably be best if I start a new thread ...

---

