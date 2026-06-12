---
title: "Ubuntu won't start - problem with my monitor??"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by KLR_rider on 2008-05-18
First off - I know almost nothing about Linux, but I'm eager to learn.  So I downloaded and burned Hardy, booted from the CD, and tried to start the demo.  It showed me the Ubuntu logo for a few seconds, the the screen went black.  My monitor gave me a message that said "OUT OF RANGE", followed by some other info.

So I went back to Windows and used Wubi to install Ubuntu.  When I rebooted and tried to start Ubuntu, the same thing happened.

Do I have to change some settings in my monitor to run Ubuntu?  I have a 17" LCD monitor, non-widescreen.

Thanks!

---

### Post by Taras on 2008-05-18
This issue may occur if the signal from the video adapter exceeds the scan range of the monitor. The video adapter setting for updating the screen (the refresh rate) is incompatible with the monitor.

[http://support.microsoft.com/kb/315614](http://support.microsoft.com/kb/315614) - Follow this link it will guide you how to do it, it is mircrosoft vista or xp, check it see if you will find solution

---

### Post by RequinB4 on 2008-05-18
This can happen either when the default ubuntu drivers for your video card aren't up to par or if X is using the wrong setting for your moniter

I'm assuming this is on the live CD.  Download the alternate cd (from [www.ubuntu.com](www.ubuntu.com), but at the download page there is a checkmark underneath the mirrors for the alt CD).  This is a text-based installer that will do the same thing but you'll not have the moniter problem.  Follow the prompts CLOSELY and be sure not to overwrite windows on the partition step!

When it is installed, boot ubuntu.  (Hopefully) You'll get an option to run in low graphics mode.  Click configure, and run with the VESA drivers.  Then you need to install the proprietary driver for your vid card - check system - admin - hardware devices.

If step 2 doesn't work, then you'll have to hit escape during GRUB (the text thing that comes up for 2 seconds) and boot "recovery mode" and input a few commands.

Also, it may help to know what moniter/video card you have

---

