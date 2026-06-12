---
title: "NVidea Driver and 11.10"
date: 2011-10-17
forum: New to Ubuntu
---

### Post by stalkier on 2011-10-17
Ok so I finally got 11.10 to install on my PC. Everything worked ok. I installed the "Recommended" NVidea driver for my graphics card and now it is stuck on a black screen upon reboot. How can I revert the driver using LiveCD? Or do I need to reinstall yet again...

I should give a bit more info. It is the non-graphical boot screen: showing pulse audio is starting up, bluetooth is starting up, etc... It gets stuck on this boot up.

---

### Post by fixerdave on 2011-10-18
you can probably let it boot to where it gets stuck and then switch to one of the console sessions (cntrl-alt-F1 to F6, F7 is the x-session).  From there, you can at least type in commands to fix various problems.  Alternatively, taping the shift key when booting might get you into the grub menu, and this may have a fallback boot without graphics.  Once you get to a console session on the machine, there are various ways to deal with video driver issues.


I'm not saying what follows is the best way... but it worked for me.  Others may chime in with a better solution.  That said, this is how I got my system past that point:  I installed the "xorg edgers" PPA.  Search for that and you'll find them.  From there, you could probably just do an update (as edgers say...) or you may wind up unistalling/reinstalling/downgrading nvidia drivers via the command-line.  Again, lots of information out there... too much really.  I'm trying to not add to the confusion by repeating everything here.

Just search for "ubuntu 11.10 sudo apt-get install nvidia" or various derivations of the above, including remove instead of install.  Find something that matches your system.  Me, I had to downgrade to the edgers nvidia-glx-173 driver to get anything... but I'm happy now.

Note that my system always has weird video issues... just a weird embedded chipset.  Such is life.

---

### Post by stalkier on 2011-10-18
> **fixerdave said:**
> you can probably let it boot to where it gets stuck and then switch to one of the console sessions (cntrl-alt-F1 to F6, F7 is the x-session).  From there, you can at least type in commands to fix various problems.  Alternatively, taping the shift key when booting might get you into the grub menu, and this may have a fallback boot without graphics.  Once you get to a console session on the machine, there are various ways to deal with video driver issues.


I'm not saying what follows is the best way... but it worked for me.  Others may chime in with a better solution.  That said, this is how I got my system past that point:  I installed the "xorg edgers" PPA.  Search for that and you'll find them.  From there, you could probably just do an update (as edgers say...) or you may wind up unistalling/reinstalling/downgrading nvidia drivers via the command-line.  Again, lots of information out there... too much really.  I'm trying to not add to the confusion by repeating everything here.

Just search for "ubuntu 11.10 sudo apt-get install nvidia" or various derivations of the above, including remove instead of install.  Find something that matches your system.  Me, I had to downgrade to the edgers nvidia-glx-173 driver to get anything... but I'm happy now.

Note that my system always has weird video issues... just a weird embedded chipset.  Such is life.

Thanks for the help. It is an older system that I pieced together from various parts from friends. Basically it is my kid's computer to play various web-based games like on Cartoon Network. Im going to try a few different variations of Linux to find one that works best. It is an AMD Athlon XP 3200+ CPU, 1GB DDR400, NVidea 6600 GT graphics card. Slower but not bad at all for a freebee.

---

### Post by wildmanne39 on 2011-10-18
Hi, I have a 6150 card and I have to use the older driver 173.

You can also probably use a momodeset parameter to boot into ubuntu then remove that driver and try another, for my card I think there was four choices and the newer ones never worked for me.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Thank you

---

### Post by anewguy on 2011-10-18
Just curious - is it getting stuck right after it says "Checking battery state....."?  I just bought a new nVidia card over the weekend because I was tired of fighting with my ATI stuff and Linux.  When I tried 11.10 I always got stuck there - nothing seemed to work except ctrl/alt/del which I actually found rather amusing.

Just curious if that is where you are getting stuck.  If so, I may try 11.10 again.  I blew it away and went back to 11.04.

Dave ;)

---

