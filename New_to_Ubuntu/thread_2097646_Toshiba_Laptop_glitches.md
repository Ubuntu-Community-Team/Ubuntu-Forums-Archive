---
title: "Toshiba Laptop glitches"
date: 2012-12-23
forum: New to Ubuntu
---

### Post by stevetsc on 2012-12-23
So here's the deal:  I've been playing with my Toshiba L775D-S7107 (Satellite L775) and I'm able to boot the Live system from a USB flash drive fine and dandy.  Everything works.  I just installed it to the hard drive and now there are problems.  The boot screen doesn't show up, no biggie.  Sometimes the login window shows up but the built-in keyboard & trackpad lock up.  Some times the login screen won't show up but the keyboard seems to still work, seeing as I can login (type password, press enter, login sound plays.)  I can't seem to use Alt+F3 to switch to a text screen.  Any suggestions?

Ubuntu 12.10 64-bit
CPU: AMD A6-3420M
GPU: Radeon HD 6520G

Thanks,
~stevetsc

---

### Post by sammiev on 2012-12-23
Are you still using 8.04? If so I think you need to try a newer version.

---

### Post by stevetsc on 2012-12-23
Haha, I should probably update my profile.  No, I'm using 12.10 x86_64
I've been toying around and it seems kind of hit or miss if it works or not.  I have been able to get logged in though.

---

### Post by stevetsc on 2013-02-10
Sorry for digging up such an old post, but I've been doing more digging on the issue.  Still with the Satellite L775D-S7107 and I've got the keyboard / trackpad working.  I found a useful post here:  [http://ubuntuforums.org/showthread.php?t=1956040](http://ubuntuforums.org/showthread.php?t=1956040)
It pretty much boils down to adding "i8042.nomux=1 i8042.reset" to your boot parameters.

I'm still having troubles getting the laptop to sleep/resume properly.  Every time the laptop enters suspend and comes back the screen stays off.  Still trying to figure that one out.  Any suggestions?  I tried the solution stated here:  [https://wiki.archlinux.org/index.php/Toshiba_Satellite_L775D_S7340](https://wiki.archlinux.org/index.php/Toshiba_Satellite_L775D_S7340)
Needless to say it didn't work.  I also tried the "laptop-mode-tools" package and that didn't do anything for me.

Thanks,
~steve

---

### Post by stevetsc on 2013-02-10
It seems that installing the proprietary driver from AMD's website has fixed the screen issue.  If you're having problems with an AMD A-series I'd suggest giving this a try.  I didn't bother with the restricted drivers through the ubuntu channel, there were 2 drivers available but with no description as far as version I just went to AMD's site and downloaded the x86_64 Linux driver.  You will need GCC to build the driver so "apt-get install gcc" before running the driver install.  I had to read the log file because on my first attempt to install I just got a nondescript error message.

---

