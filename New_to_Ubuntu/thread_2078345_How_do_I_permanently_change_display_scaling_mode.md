---
title: "How do I permanently change display scaling mode?"
date: 2012-10-30
forum: New to Ubuntu
---

### Post by HeWhoIsCalledB on 2012-10-30
I run several old Windows games (from GOG.com) in Wine on my laptop running Ubuntu 12.04 (amd64).  All of these games run in 4x3 resolutions; usually 800x600 but sometimes 640x480.

My laptop's screen has a native resolution of 1366x768 (16x9) so I need to change the scaling mode from "Full" (the default) to "Full aspect" (I already know how to do this in the command line using xrandr) or my 4x3 game will be stretched across my 16x9 screen.  I would much rather have black bars on either side of my game than have a stretched image.

My issue is that after I reboot, the display scaling mode reverts to "Full" which means I need to open a terminal and change it to "Full Aspect" every time I want to play one of my games.

I assume there is some config file hidden in my system that I can edit to change the default scaling mode to "Full aspect."  If someone could point me there and tell me how to edit it, I would be much appreciative.

My GPU is an ATI Mobility Radeon HD 4250, and I'm using the FOSS driver.  The games I play are old enough that they do not require the proprietary driver from AMD.

Thanks much!

---

### Post by HeWhoIsCalledB on 2012-11-01
I tried adding the following line to /etc/rc.local

```
xrandr --output LVDS --set "scaling mode" "Full aspect"
```

and then rebooted, then ran the command

```
xrandr --prop
```

to make sure it worked, but it did not work, the scaling mode was still "Full" after rebooting, when I wanted it to be "Full aspect"

The command I added to /etc/rc.local does do what I want it to, but only when I run it myself, it seems.

Any help would be appreciated.

It's possible this thread belongs in another forum; I posted it here because I am new to Linux (despite being generally technically inclined) and my brain is mush from using Windows for 20 years.  If this question would be best answered in another forum, I would much appreciate a moderator moving it.  Thanks much!

---

### Post by HeWhoIsCalledB on 2012-11-01
I have solved my problem.

I ended up making a shell script (named .properscaling.sh) which I placed in my home directory.

The script contained only one command:

```
#!/bin/bash
xrandr --output LVDS --set "scaling mode" "Full aspect"
```

Then I listed it as a startup application in Unity (bash /home/brendan/.properscaling.sh).

Now I can play my games without needing to type a command in the terminal first.

:D

---

