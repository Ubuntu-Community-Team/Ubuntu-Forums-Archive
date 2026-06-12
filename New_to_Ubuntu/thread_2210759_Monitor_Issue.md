---
title: "Monitor Issue"
date: 2014-03-12
forum: New to Ubuntu
---

### Post by sadamitus303 on 2014-03-12
[COLOR=#000000][FONT=verdana]I'm trying to get my external monitor to work with my HP laptop while running Ubuntu 13.10 (it works fine on Windows). When I plug it in while Ubuntu is running, it doesn't recognize it at all. When I have it plugged in before I boot my computer, a strange white screen pops up with a blinking black cursor in the top left (typing doesn't seem to do anything). However, when I am on this screen and I press the power button on my laptop, some strange distorted black text appears as it powers down.[/FONT][/COLOR][COLOR=#000000][FONT=verdana]The only way I have gotten the monitor to work is plugging it in after the GRUB menu appears, but before I select to boot Ubuntu.

Also, whenever I go into suspended mode, upon reawakening my computer, the display stops working/ isn't detected anymore.

Not sure if this info will help, but here's output from a couple commands..

[/FONT][/COLOR]
**[COLOR=#000000][FONT=verdana]xrandr -q:[/FONT][/COLOR]**
[COLOR=#000000][FONT=verdana]xrandr: Failed to get size of gamma for output default Screen 0: minimum 640 x 480, current 1920 x 1080, maximum 1920 x 1080 default connected primary 1920x1080+0+0 0mm x 0mm 1920x1080 0.0* 1280x1024 0.0
1024x768 0.0
800x600 0.0
640x480 0.0[/FONT][/COLOR]
**[COLOR=#000000][FONT=verdana]xrandr --auto :[/FONT][/COLOR]**
[COLOR=#000000][FONT=verdana]xrandr: Failed to get size of gamma for output default

Thanks! :)[/FONT][/COLOR]

---

### Post by sadamitus303 on 2014-03-13
Shameful bump

Found another problem. When I log out, I get a blank screen of the same color of my background. I hear the log in sound prompt (if that makes sense), but I can't get the screen to show up or log in.

---

