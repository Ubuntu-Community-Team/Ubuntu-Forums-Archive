---
title: "Saving ARandR settings across reboot Lubuntu 20.04"
date: 2020-06-25
forum: New to Ubuntu
---

### Post by nginmu on 2020-06-25
I have a 1600 x 900 HP G72 laptop with HDMI output for 2nd monitor. My 2nd monitor is 1920 x 1080 Samsung LCD positioned to the immediate left of the laptop with the bottom of the screen about an inch or so higher than the bottom of the laptop screen.

I am using ARandR to adjust the positions.

All works well but I have to reset the positioning every time I reboot.

I can save the layout as a .sh file;

```

#!/bin/sh
xrandr --output LVDS-1 --primary --mode 1600x900 --pos 1920x180 --rotate normal --output VGA-1 --off --output HDMI-1 --mode 1920x1080 --pos 0x0 --rotate normal --output DP-1 --off

```

How can I get this layout to be automatically adopted by the system every time it boots?

---

### Post by ActionParsnip on 2020-06-25
If it doesn't need sudo to run the script (Note that file extensions don't mean much in Linux), there is an item in settings for startup items and you can make your script run at logon.

---

### Post by nginmu on 2020-06-25
preferences > lxqt settings > session settings > autostart

. did the trick

not sure why but I had to set it to run 2 scripts, one immediately and one with 'wait for system tray' checked. 1st script with laptop monitor set a little lower than the external monitor, then 2nd script with both monitors on same baseline.

if I didn't do it this way, the positioning was 'off' with parts of the desktop present but unreachable with the mouse, and all my shortcuts were on the right hand laptop lcd.

running it twice as above resulted in a perfect display, everything visible and mouseable and all icons on the left hand external monitor

---

### Post by ActionParsnip on 2020-06-26
Awesome. Please mark as solved :)

---

