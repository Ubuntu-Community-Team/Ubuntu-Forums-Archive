---
title: "Problems with scaling and AMD control center on video"
date: 2014-05-21
forum: New to Ubuntu
---

### Post by Mazate on 2014-05-21
I'm using Ubuntu 14.04 and just installed Catalyst 14.10 successfully.  As usually happens after installing a new AMD video driver, my visible screen on my monitor doesn't take up the whole screen.  I have a black border around the edges of my screen.  Normally I go into the catalyst control center and adjust the screen with the scaling options and the problem is solved.  In this version of the catalyst control center, there are no scaling options.  It's just a drop down menu to select the option to have the screen take up the whole size of the monitor, which is already selected by default.  Any help is most appreciated.

---

### Post by SingingBush on 2014-05-21
as per this thread: [http://ubuntuforums.org/showthread.php?t=2225312](http://ubuntuforums.org/showthread.php?t=2225312)

**sudo amdconfig --set-pcs-val=MCIL,DigitalHDTVDefaultUnderscan,0**

---

