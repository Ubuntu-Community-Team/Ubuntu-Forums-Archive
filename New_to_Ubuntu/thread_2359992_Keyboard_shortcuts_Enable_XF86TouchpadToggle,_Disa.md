---
title: "Keyboard shortcuts: Enable XF86TouchpadToggle, Disable Super+P, Disable Super+T"
date: 2017-04-30
forum: New to Ubuntu
---

### Post by bolshaya on 2017-04-30
[FONT=arial]Hi,

I have some problems enabling/disabling certain keyboard shortcuts on Ubuntu 16.04 LTS. Note that I have tried the "System Settings --> Keyboard --> Shortcuts" route and "CompizConfig Settings Manager" to solve these.

**1. Disable Super+P.**
I would like to disable the default Super+P behaviour (cycle through multi-monitor modes) in order to assign a different function (launch display setting dialog). In case there is a way to replace the Super+P behaviour with something more interactive (like in Windows), that might work as well. Otherwise I would like to call "unity-control-center display" if Super+P is pressed.

**2. Disable Super+T.**
I would like to use Super+T for opening the terminal instead.

**3. Assign intended function to XF86TouchpadToggle.**
My Laptop (Lenovo Y50) has the key function Fn+F6 which serves to toggle the touchpad state. Unfortunately it does not work in Ubuntu. I read that *dmesg|tail -5* tells me whether a key is mapped. It wasn't. I tried to map it to *keycode 199 = XF86TouchpadToggle NoSymbol XF86TouchpadToggle *with *sudo setkeycodes e073 199 *which, according to *showkey -k* worked. However, the touchpad toggling still does not work. I then tried to define a keyboard shortcut in the system settings dialog but it doesn't recognize [FONT=arial]*XF86TouchpadToggle. *The CompizConfig Settings Manager also does not recognize this key.
If the key got recognized, I could run the following script, I found online (it works for me):
```
#!/bin/bash

read TPdevice <<< $( xinput | sed -nre '/TouchPad/s/.*id=([0-9]*).*/\1/p' )
state=$( xinput list-props "$TPdevice" | grep "Device Enabled" | grep -o "[01]$" )

if [ "$state" -eq '1' ];then
    xinput --disable "$TPdevice"
else
    xinput --enable "$TPdevice"
fi
```

I've read a bit online about all these problems and so far I'm not very confident about solving 1 and 2. But perhaps there's a solution to 3?
[/FONT][/FONT]

---

### Post by krzysiek-t on 2017-10-02
Ad.3. I had a similar problem - wanted to have a key binding working like a special key for toggling the touchpad. Refer to my article: [https://artofcode.wordpress.com/2017/10/01/how-to-add-a-key-binding-to-toggle-a-touchpad-under-linux/](https://artofcode.wordpress.com/2017/10/01/how-to-add-a-key-binding-to-toggle-a-touchpad-under-linux/)

---

