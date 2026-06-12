---
title: "Resolution wrong, dancing white pixels, screen out of range, cartoon images"
date: 2014-08-12
forum: New to Ubuntu
---

### Post by locky3 on 2014-08-12
Hello, I've spent hours looking for help to no avail.  A couple weeks ago I dropped my laptop on carpet while it was on, but it was fine.  I hibernated it that evening and for the next 3 nights.  Still no problems. Then one night I powered it down instead of hibernating. The next morning when the computer loaded the screen was messed up, the colors are too bright, there are white pixels dancing around, images are cartoonish.  Also, the computer thinks the screen is about 3 times bigger than it is and so part of it is out of range. The font/icons/applications are all normal size.

As the damage did not show right away, I am hopeful that it is a software issue.

Here is what I tried:
1. I went to Display Settings and tried to change the resolution.  The computer says it is at 1280x1024. None of the other selections helped, they all made it even larger.

2. I used the xrandr command to try to force the correct 1024x600 resolution.  That left the screen out of range and made the font/icons/applications huge, it only lasted a moment and reverted itself back to the 1280x1024 resolution.  Afterward this is what xrandr showed me:

[FONT=times new roman][SIZE=2]$ xrandr
Screen 0: minimum 320 x 200, current 1280 x 1024, maximum 32767 x 32767
LVDS1 connected primary 1280x1024+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1280x1024      59.7*+
   1280x960       60.0  
   1152x864       60.0  
   1024x768       60.0  
   800x600        60.3     56.2  
   640x480        59.9  
   1024x600_60.00   59.9  
VGA1 disconnected (normal left inverted right x axis y axis)
   1024x600_60.00   59.9  
VIRTUAL1 disconnected (normal left inverted right x axis y axis)[/SIZE][/FONT]

3. Curious, I used xrandr commands to attempt to force a 2048x1200 resolution.  This only gave me an error message:

[FONT=times new roman][SIZE=2]$ xrandr --addmode LVDS1 2048x1200_60.00
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  30
  Current serial number in output stream:  31[/SIZE][/FONT]

4. I've tried many more things, downloading a new graphics driver was one, and nothing seems to make any difference.  I only have Ubuntu 14.04 32-bit intalled on my Toshiba NB505, otherwise I'd test my netbook on Windows.  My understanding is that if you only have Ubuntu it is imposible to then add Windows.  I was thinking of erasing my hard drive to add Windows, but I am afraid as I can't even see the GRUB drive. When I hold down the Shift key I know it comes up, but all I see is lines, trying to install another operating system with no gurantee of being able to read the screen is a bad idea.

Anyone have any ideas?  I have used Ubuntu for a couple of years, but haven't had to mess around with it much, so I do consider myself a newbie still, maybe an intermediate one.
Thank you, Locky

---

### Post by Impavidus on 2014-08-12
Physical impacts cause hardware errors, usually not software errors. As a result of a hardware error the system may be unable to properly query the hardware for it's capabilities. The system does this on reboot, inbetween, like when hibernating, this information is cached. So I suspect a hardware problem.

Try booting from a live disk. If you get the same problem, it's not your software. BTW, it is possible to install Windows as dual boot on a system with Ubuntu already, but it won't help you solve this problem.

---

### Post by locky3 on 2014-08-21
Solved - I kept trying to play around with anything I could think of, mostly from the bootup menu.  I wanted it to boot in a system repair mode, but the screens at startup were just lines, so I had no idea what they were.  I think I might have been able to find my way to the system repair on the grub menu, I let it run (which was also just a bunch of lines, but the computer sounded like it was doing something) for hours.  Then I got tired of it and turned it off manually.  I did this a couple times and then tried again to use my computer, it still had the same problems - cartoon images, dancing white pixels, wrong resolution...

Then I left it off for about 24 hours.  When I turned it on today I couldn't believe my eyes, it is competely back to normal!  In conclusion, it was definately a software problem that somehow fixed itself, Praise the Lord, I was not looking forward to buying something new or trying to fix any hardware.

---

