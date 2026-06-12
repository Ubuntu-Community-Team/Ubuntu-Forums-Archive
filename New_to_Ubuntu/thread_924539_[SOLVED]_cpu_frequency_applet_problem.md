---
title: "[SOLVED] cpu frequency applet problem"
date: 2008-09-19
forum: New to Ubuntu
---

### Post by iansane on 2008-09-19
Hi, I added the cpu frequency applet (one for each core). I then did the 
"sudo dpkg-reconfigure cpufreq-applet" command and gave the applet root priveleges. It appears to be working but when I choose performance it says it's in "performance" mode but it is acting like "on demand" mode, only using 1Ghz (45%) of the max possible 2.20 Ghz.

This is a fresh installation of Ubuntu 8.04 32 on a AMD 64 machine. With the last install I would set it to performance and it would shoot up to 2.20Ghz . I do this when running vm's on VirtualBox because regardless of the fact that on demand is supposed to go up when needed, it doesn't. This way I have full throttle at all times and my vm's run better.

I had powernowd installed. I tried cpufreqd and it removed powernowd. I read other posts on how to set it in command line and how to make it permanent but i want to be able to change it from the applet and on my last install it just worked.

Amazing all the things that just worked on the last install because it was BETA Server AMD64 with gnome-desktop and about 20 kernel updates. Tons of 3rd party 32 and 64 bit apps installed. Disaster waiting to happen. :-)

Can someone tell me exactly what packages need to be installed for this cpufreq-applet to work right? And then how to make it work from the applet like it used to?

Thanks

---

### Post by iansane on 2008-09-19
confirmed by looking at system monitor. It goes up and down like its set at on demand governor when the applet says performance. Applet is not really changeing it and stays at 1GHZ

---

### Post by iansane on 2008-09-20
well I guess this isn't a well known topic or the forums aren't busy tonight.

After going through this tutorial

[http://ubuntuforums.org/showthread.php?t=248867](http://ubuntuforums.org/showthread.php?t=248867)

removing powernowd and cpudyn, adding all the modules then restarting, then doing the "dpkg-reconfigure gnome-applets" thing and then adding the applets again, all in the right order, the problem is fixed.

I didn't have to go through all of this on my last install and don't know why.

Oh well, problem solved.:-)

---

