---
title: "100% CPU + low RAM usage"
date: 2012-05-16
forum: New to Ubuntu
---

### Post by CswP on 2012-05-16
i have just recently installed Ubuntu for the 1st time. Everything has been working great, but i have noticed that my CPU usage is much higher than it was while running Vista. I have looked endlessly the last few days for a solution, but no one else seems to have these 2 issues at the same time!!
what is most distressing is that this is happening while running videos on youtube or just simple web browsing like on these forums now... my CPU will max out at 100%.. sometimes occasionally jumping down into the 70s.. all the while my RAM usage never goes above 1.2gb of 3.7gb. Also, while i'm simply idling on the desktop doing nothing with everything closed... my CPU continuously jumps between 15%-50%. In Vista, I could run demanding games like Star Wars The Old Republic, and even PVP smoothly and stay within 85-95% CPU and roughly 3.5gb RAM used... and would Idle at 1-4% CPU. It seems like Ubuntu doesn't want to utilize all of the RAM that is there.. even tho it recognizes it. Please help!! :)
I'm on a Laptop..

HP Touchsmart tx2
Ubuntu 12.04 LTS **64bit**
AMD Turion X2 Ultra Dual-core Mobile ZM-82  2.2GHz
4GB DDR2 RAM
ATI Radeon 3200 (VESA: RS780M Graphic Driver)

---

### Post by anewguy on 2012-05-16
Usually things aren't as memory "heavy" in ubuntu from my observations.  Keep in mind the kernel uses some of the memory.

As far as CPU usage goes, that's got me a little buffalowed.  Have you run "top" in a terminal window to see what is using your CPU?   That is where I would start so I'd at least have an idea of what processes are using what percentage of the cpu.

---

### Post by Ubun2to on 2012-05-16
If all else fails, just use Unity 2D by clicking on the Ubuntu icon on the logon screen (next to your name), and selecting Unity 2D.

---

### Post by CswP on 2012-05-16
but my cpu shouldnt max out doing basic things...  weather im idle or trying to watch a video and web surf, my RAM  never goes outside of 1 - 1.2gb usage but my CPU will just be maxed to 100% at the same time.. this is not right.
why is it not utilizing my RAM and maxing out my cpu?

---

### Post by alphacrucis2 on 2012-05-16
You need to determine what is actually using the cpu. Use top or the system monitor.

---

### Post by anewguy on 2012-05-16
> **CswP said:**
> but my cpu shouldnt max out doing basic things...  weather im idle or trying to watch a video and web surf, my RAM  never goes outside of 1 - 1.2gb usage but my CPU will just be maxed to 100% at the same time.. this is not right.
why is it not utilizing my RAM and maxing out my cpu?

This is why I suggested running top.  Run it when you aren't going anything and see what process is using the most CPU.  Do the same thing in each scenario where your CPU usage is up.  Just because you aren't running anything there are still any number of processes still running your PC.  It's also possible that something is running in the background that is not needed and can be terminated.

Also keep in mind - if you use the system monitor to check things it is like most of those type of tools have been pretty much forever:  CPU hogs.  You will DEFINETLY see a large jump in CPU usage when it is running - it's just the nature of the beast.  That is another reason to use top - it's not the resource hog that a system monitor can be.

Also, try ps -e > testjnk.txt then post a reply here and attach the testjnk.txt file (it will be in your home folder).

Also, CPU usage isn't directly tied to memory usage - even when swapping is high the CPU spends a lot of time just waiting on I/Os.  So, the question would be:  does your swap file usage go up when your internal memory usage is what you think is low?

Dave ;)

---

### Post by CswP on 2012-05-16
using HTop it appears that my CPU is being used up by 2 processes:

compiz
&
 /usr/bin/X :0 -nolisten tcp vt7 novtswitch (what ever this is)

between these 2 processes alone they are sucking up like 50-70% of my cpu

---

### Post by anewguy on 2012-05-17
Try ubun2to's suggestion above for trying 2d Unity.  If that doesn't make much difference post back and we can go from there - you may even want to try installing the package "gnome-shell" package, then log out, and when it presents the log in screen again, select the gnome-shell first, then enter your password and finish logging in.  See if it reduces usage at all (I don't know if it will or not).

Post back your testing and results.

Dave ;)

---

