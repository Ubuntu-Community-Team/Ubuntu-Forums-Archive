---
title: "[SOLVED] Dual-monitor setup for Ubuntu"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by Motorhead Kaze on 2008-06-26
Hi, I tried posting this under "Desktop Environments" but not sure if that is the right place to get answers. (I posted yesterday, but no hits so far).

Anyway, I just bought a second monitor and got an ATI, Radeon dual-head video card. Ubuntu was cool to suggest an ATI driver for me and I installed it. Both monitors are working, one on a digital cable and the other on an analog cable. The second screen of course is still just a clone of the first. Is there a menu I need to tick off a box to split the monitors, or download a program? (Just for info -- so you know the hardware works -- I dual boot XP and Hardy, and the extended monitor/dual monitor is working very nicely on the XP side.)

I read several other posts about this, saw some help for Nvidia users, a guy saying that he thought ATI users were out of luck, and a very lengthy tutorial about dual-monitor setup from 2006, but I guessing there must be an updated method.

What is the easiest and correct way to make the second monitor an extension of the first? I.e. one large desktop?  

Thanks much for the help!

---

### Post by roffemuffe on 2008-06-26
I haven't tried it on Linux, but I did a search for your problem:


This didnøt work for the guy asking, but you could be the lucky one.
[http://ubuntuforums.org/showthread.php?t=22598]("http://ubuntuforums.org/showthread.php?t=22598")

Otherwise consider it a friendly bump, hoping some techie sees it soon :KS

---

### Post by Motorhead Kaze on 2008-06-26
Thanks anyway Roffemuffe.

This is what finally worked for me```
gksudo gedit /etc/X11/xorg.conf
```and add the red text.
```

Section "Screen"
        Identifier      "Default Screen"
        Device          "Configured Video Device"
        DefaultDepth    24
       [COLOR="Red"][B] SubSection "Display"
            Depth           24
            Virtual         2560 1024
        EndSubSection[/B][/COLOR]
EndSection
``` then I restarted X, went into system/preferences/screen resolution and unchecked the cloned screens box, pulled the monitor (white square) marked "Electronics" off to the left, selected the resolution, 1280x1024 at a refresh rate of 60hz and on the monitor to the right (another white square) marked "BenQ 19in" I selected the same resolution and refresh rate.  Apply, close.

Now I have dual monitors on Ubuntu Hardy.

Another issue: "...the unchecked box getting rechecked is a bug that involves a file in your home directory called ~/.gnome2/monitors.xml,  which sometimes doesn't get overwitten properly. That's one reason deleting all the .g stuff worked. If the problem comes back, try deleting that file, resetting the stuff in that dialog, and restarting"

Note 2: Anyone who has trouble with finding what the Virtual numbers should be &#8594; add the widths of your 2 monitors (for me, 1280+1280=2560) to get the first number, and the 2nd number is the greater height of the 2 monitors (for me, both are the same, so the number remains 1024) hence my virtual number was 2560 1024

UPDATE!  Upon a fresh install of HARDY I could not get dual monitors to work, nor would Ubuntu recongize my second monitor. I had turned ON propriety driver for my ATI graphics card and THAT made Ubuntu unable to see the monitor. So, switch that bugger OFF in system/admin/hardware drivers before trying to set up those dual monitors using ATI!

---

