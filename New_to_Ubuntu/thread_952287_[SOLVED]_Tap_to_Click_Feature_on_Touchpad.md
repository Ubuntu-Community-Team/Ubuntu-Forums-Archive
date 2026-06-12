---
title: "[SOLVED] Tap to Click Feature on Touchpad"
date: 2008-10-19
forum: New to Ubuntu
---

### Post by Sparty26 on 2008-10-19
Hey, I was wondering if there was some way to turn off the "tap to click" function on my touch pad in kubuntu? I can't seem to find it because it is not in the mouse settings. Any help?

---

### Post by anjilslaire on 2008-10-19
edit your xorg file

```

sudo kate /etc/X11/xorg.conf

```

Then add the bold line in the appropriate section:
```

Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "HorizEdgeScroll" "0"
**Option "TapButton1" "0"**
EndSection

```

Then restart the X server, via ctrl+alt+backspace.

---

### Post by Sparty26 on 2008-10-19
That doesn't seem to do the trick for me. Is something supposed to pop-up when I hit ctrl+alt+backspace, because nothing appears to happen when I do that?

---

### Post by anjilslaire on 2008-10-19
That should restart your whole GUI. Hold all 3 buttons down simultaneously. If that doesn't happen, restart your system to be sure it goes down, or log out & in the system menu select 'Restart X server".

Be sure you saved the xorg.conf file after adding that line too, of course.

---

### Post by Sparty26 on 2008-10-19
Yep, that fixed it. I restarted it by logging out, THanks for the help.

---

