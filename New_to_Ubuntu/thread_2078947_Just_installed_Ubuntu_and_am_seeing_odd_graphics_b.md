---
title: "Just installed Ubuntu and am seeing odd graphics bugs"
date: 2012-11-01
forum: New to Ubuntu
---

### Post by Demiknight on 2012-11-01
Hi, I just installed Ubuntu 12.10 for the first time, and as the title says I am seeing some weird glitches. It appears to be some weird type of artifacts over text and images. It appears over my url bar in chrome and the bookmarks, as well as over some items in the Software Center, including the images at top. As a note, when I install something in the Software Center, the rotating arrows of the progress icon appear as a rotating version of the glitched image on the other icons. I'm including picture examples of all of this below.

I am using an Nvidia Geforce 560 Ti and the drivers that came with the installation. I am pretty sure this is the Nouveau driver, but I can get more details if someone can tell me how.

[image 1]("http://i.imgur.com/lBZnB.png")
[image 2]("http://i.imgur.com/oC4h8.png")
[image 3]("http://i.imgur.com/rSWdg.png")
[image 4]("http://i.imgur.com/IRPW8.png")

---

### Post by pompel9 on 2012-11-01
Try to use the proprietary driver and see if that solves the problem.

I have the same problem, but I can't use the proprietary driver because it broke my system when I installed it. Had to go into recovery mode and reinstall Nouveau driver.
Just a warning, that it can brake your system. So if you decide to install it, be ready for the worst.

Good luck.

---

### Post by Demiknight on 2012-11-01
The problem with installing the proprietary driver is that nothing appears when I go into Additional Drivers under Software Sources.

When I try to install the .run file that I got from Nvidia itself, some weird things happen. First I get an error telling me the X server is running. So I press ctrl-alt-f1 to try and do it from there. When I turn off the X server and run the driver file, it tells me that it can't install while the Nouveau driver is still running, and offers to create a .config file to disable that driver. I said yes to this.

After the computer restarted, the screen appeared in a 1024 resolution, which I assume is because the driver was disabled. But when I pressed ctrl-alt-f1, I just got a blank screen instead of the full screen terminal. Pressing enter a few times or typing one letter a lot in order to find the cursor if it was off screen didn't work. I then went back into the normal desktop and deleted that config file to restore the Nouveau driver, at least temporarily.

This is where I am now, so I don't know what to do. If there's a better way to install the proprietary driver, I'll gladly do that, but I don't know what to do right now.

---

### Post by Demiknight on 2012-11-11
I figure I should update this since I have figured out the cause. It was in fact the graphics driver, and installing the proprietary nvidia driver fixed the issue.

The problems I was having with the nvidia drivers were due to missing kernel headers and other things I needed to create the module.

---

