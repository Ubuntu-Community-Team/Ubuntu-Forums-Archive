---
title: "Touchpad is copy/pasting by itself?"
date: 2008-10-09
forum: New to Ubuntu
---

### Post by skroops on 2008-10-09
For some reason my touchpad pastes when I quickly tap the upper right corner (which means it happens when I accidentally bump it in the middle of typing, *all the time*).

I have a genuine synaptics touchpad but there is nothing in xorg.conf that seems out of the ordinary.  This behavior is really annoying, can anyone help me to disable it?

---

### Post by tjwoosta on 2008-10-09
strange...

i have a synaptics touchpad but nothing like that happens to mine

do you have the synaptics touchpad driver installed?

```
sudo apt-get install xserver-xorg-input-synaptics
```

---

### Post by skroops on 2008-10-09
```
Reading state information... Done
xserver-xorg-input-synaptics is already the newest version.
xserver-xorg-input-synaptics set to manually installed.

```

---

### Post by tonymoloney on 2008-10-09
This sort of thing used to drive me up the wall until I found out that i could alter the sensitivity of the touchpad in the BIOS of my laptop. Once I did that, no more problems.

---

### Post by schauerlich on 2008-10-09
When you click the wheel on a normal mouse, whatever is highlighted or the last thing in the clipboard will be pasted. You might have the top right corner of the track pad set to simulate the wheel click. Can you post your xorg.conf?

---

### Post by minky311 on 2008-10-09
You could also go to system->preferences->mouse and click on the touchpad tab. Once there you could uncheck **enable mouse clicks with touchpad**.
That is if you don't really use that option.

---

### Post by Ripfox on 2008-10-09
gsynaptics is in the repos as well.

---

### Post by skroops on 2008-10-10
> **EDavidBurg said:**
> When you click the wheel on a normal mouse, whatever is highlighted or the last thing in the clipboard will be pasted. You might have the top right corner of the track pad set to simulate the wheel click. Can you post your xorg.conf?

OK, I was thinking it was something like that.

xorg.conf:
```
Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
```As you can see the touchpad isn't there.  I recently installed intrepid so I don't know if it's handling mouse settings differently.  There was an entry for it when I was running hardy, and it was a standard synaptics block.  (The problem was present in hardy as well)

I'm going to look around and see if I can figure out if intrepid is handling mouse input differently, thanks for pointing me in the right direction.

Relevant output of *xinput list*
```
"SynPS/2 Synaptics TouchPad"    id=3    [XExtensionPointer]
    Num_buttons is 12
    Num_axes is 2
    Mode is Relative
    Motion_buffer is 256
    Axis 0 :
        Min_value is 0
        Max_value is -1
        Resolution is 1
    Axis 1 :
        Min_value is 0
        Max_value is -1
        Resolution is 1

```

> gsynaptics is in the repos as well.Thanks for the tip.  I'm wondering if that will just edit the apparently irrelevant xorg.conf though.

> uncheck **enable mouse clicks with touchpad**.
That is if you don't really use that option.I really don't want to give up tap-to-click, thanks though.

---

### Post by schauerlich on 2008-10-10
> **skroops said:**
> OK, I was thinking it was something like that.

xorg.conf:
```
Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection
```

You should have a section in your xorg.conf that related to the keyboard, the mouse, language settings, etc. Try ```
sudo dpkg-reconfigure xserver-org
``` to rebuild your xorg.conf with that sort of information.

---

### Post by skroops on 2008-10-10
I ran it, but it just outputted the same file

---

