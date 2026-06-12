---
title: "Problems with Dual Monitor setup and nvidia X server"
date: 2014-12-16
forum: New to Ubuntu
---

### Post by The_Craft on 2014-12-16
[SIZE=3]      Three days ago I broke my computer screen... [SIZE=2]since  I am a student I have to constantly deliver paperwork so I do not have  enough time to take it to an IT and just have it fixed. So I thoughted  about plugging [/SIZE][/SIZE]my computer 
(with a **d-sub cable[ATTACH=CONFIG]258632[/ATTACH]**) to another screen and **just roll with it**. But here is the problem. **The screen is extended not cloned.**[ATTACH=CONFIG]258633[/ATTACH]
I google and fumbled around but it seems that I do not know enough about computers to solve the problem.

On **nvidia-settings** this is the screen I have (since this is a screenshoot you will be able to see how my computer is perceiving the two screens):
[ATTACH=CONFIG]258634[/ATTACH]

This is the information ubuntu gives me through the '**lspci**' command:
[ATTACH=CONFIG]258635[/ATTACH]

Other general info:
My computer is an Asus model: AR5B125
It's video card is an nvidia GEFORCE GT
It`s running the latest version of ubuntu and it's drivers are all up to date. (Driver is nvidia 331)

Thank you for your attention.

---

### Post by The_Craft on 2014-12-18
**Problem solved. I disabled the laptop screen through the "*xrandr*" command.**
[HR][/HR]thexxxx@thexxxx-X66XX:~$ sudo xrandr
[sudo] password for thexxxx: 
Screen 0: minimum 8 x 8, current 3286 x 1080, maximum 16384 x 16384
LVDS1 connected 1366x768+0+0 309mm x 174mm
   1366x768       60.0*+
   1360x768       59.8     60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
VGA1 connected 1920x1080+1366+0 477mm x 268mm
   1920x1080      60.0*+
   1680x1050      60.0  
   1600x900       60.0  
   1280x1024      75.0     60.0  
   1280x800       59.8  
   1152x864       75.0  
   1280x720       60.0  
   1024x768       75.1     60.0  
   832x624        74.6  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  
HDMI1 disconnected
DP1 disconnected
VIRTUAL1 disconnected
**[SIZE=2](Following the logic that the tv screen is bigger then the laptop screen that gives me LVDS1 as the laptop and VGA1 as the tv[/SIZE]**)
thexxxx@thexxxx-X66XX:~$ sudo xrandr --output LVDS1 --off
[HR][/HR]**And that solved the problem.** **Right now I have my tv screen displaying the desktop/ubuntu unix and other applications perfectly.**

---

