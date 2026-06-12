---
title: "[solved] Limit max available resolution"
date: 2021-11-23
forum: New to Ubuntu
---

### Post by Tadaen_Sylvermane on 2021-11-23
When I'm away for x amount of time my resolution switches to 4k. I'd like to make it so the machine can't even acknowledge any resolution above 1080p. How can I restrict that?

---

### Post by KBar on 2021-11-23
Are you running Ubuntu on X11 or Wayland?

---

### Post by LokiScarlet on 2021-11-24
Sorry, but I have to answer this question with a question.

Do you need the resolution to stay at 1080p for performance reasons? Or does 4K just make everything too small?
Because if it's the latter, you can go to Settings > Accessibility and turn on Large Text. It typically scales up everything that's either text or sized relative to text. It's basically HiDPI mode. I learned this the hard way when I got my 4K monitor.

---

### Post by Tadaen_Sylvermane on 2021-11-24
The reason is to small + my gpu is an rx570. It's got muscle but not enough to drive 4k for the games I like to play. That and I've eliminated my desk for a 55" tv about 10ft (3m) away as I don't use my computer as much as I used to these days. Then to top it off my sight is going a bit so I can't honestly see much difference between 4k and 1080p. Figure why upgrade (especially with gpu prices these days) when I can just lock the resolution :)


X11. And I did find a solution just this morning. Involved a custom xorg.conf file

```
jason@homewrecker:/usr/share/X11/xorg.conf.d$ cat 90-resolutionlock.conf 
Section "Screen"
    Identifier  "Default Screen"
    Device      "Radeon RX570"
    Monitor     "HDMI Output"
    DefaultDepth    24
    SubSection "Display"
        Depth       16
        Modes       "1920x1080" "1600x900" "1366x768"
    EndSubSection
    SubSection "Display"
        Depth       24
        Modes       "1920x1080" "1600x900" "1366x768"
    EndSubSection
EndSection


Section "ServerLayout"
    Identifier "Maximum Resolution"
    Screen "Default Screen"
EndSection
```

This had the unexpected benefit of also affecting my lightdm login screen which was quite difficult to see  from where I typically park myself when I'm using the machine.

*EDIT* For more explanation I should mention this is not a standard Ubuntu installation. I installed via debootstrap from my pxe server. I'm trying to keep it as minimal as possible. I'm assuming I'm missing a package that normally prevents this issue I'm having / had. ```
apt install xfce4 --no-install-recommends
``` among other things. Doesn't have all the usual bells and whistles one might expect. It's set up with the Xanmod kernel and Lutris through which I run World of Warcraft. Also running Steam stuff via Proton. I had some issues awhile back with this but since I switched to a single screen they've all resolved. Odd considering the 2 screens weren't even on the same gpu (side screen was on motherboard gpu). Regardless at this point I'd say my performance is better than Windows ever was for both WoW & Skyrim. Even Java Minecraft is notably better. Combine that with ability to run a script vs paying 30-50 bucks a year for a backup program. Can't lose.

---

