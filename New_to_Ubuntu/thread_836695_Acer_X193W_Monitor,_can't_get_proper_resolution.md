---
title: "Acer X193W Monitor, can't get proper resolution"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by Joseph Elliott on 2008-06-21
I just bought a new monitor (Acer X193W) and I can't get the widescreen resolution (1440x900) that its suppose to have.  The biggest I get is 1152x864.  How do I fix this?

---

### Post by N.N. on 2008-06-21
First you might want to try the graphical configuration utility displayconfig-gtk. To launch this tool, issue the following command in a terminal: ```
gksudo displayconfig-gtk
``` Once the application is open, try correcting the problem by selecting the correct model of your monitor in the "monitor" tab. (Sorry if these instructions are a bit vague, I'm not using Ubuntu at the moment.)

If you can't solve the problem from this graphical utility, you might try manually specifying the specifications of your monitor in your /etc/X11/xorg.conf file. You need to specify the horizontal and vertical frequency ranges of your monitor in this file. These ranges can often be found in the User's Manual that came with your monitor or by doing a Google search. For more information on how to find them and for detailed instructions for specifying them in the /etc/X11/xorg.conf file, see the following link: [https://help.ubuntu.com/community/FixVideoResolutionHowto#head-e2249d4bcb9fe0dea110f9b82ec7a40716221541](https://help.ubuntu.com/community/FixVideoResolutionHowto#head-e2249d4bcb9fe0dea110f9b82ec7a40716221541).

---

### Post by Joseph Elliott on 2008-06-21
Thanks that worked perfectly.

---

### Post by shanedj on 2009-04-07
Hi Joseph, 

I have the same monitor, can you post the lines that you put in the xorg.conf

Thanks

Shane

---

### Post by ChRe on 2010-02-15
I spent the last two days trying to get my acer x193w monitor to work at its spec resolution of 1440x900, failing at fiddling around with the xorg.conf file, not knowing what I was doing wrong.  Today, on a whim, I started messing with the buttons on the monitor.  The monitor has five modes--user, text, standard, graphics, and movie.  The mode my monitor was on was "movie".  I changed this to the "user" mode, and all of a sudden ubuntu could detect the monitor where it could not detect it before and everything just worked.  No xorg.conf file info needed at all, it just worked.  If any other people with this monitor have problems, maybe it could be the same problem as I had--monitor in wrong mode.  So try that and hopefully it might save someone lots of headache.

---

### Post by wbrb on 2010-04-14
Thank you so much ChRe.

I have a Radeon 9200SE and an Acer x193w and VGA (not DVI) with Lucid / 10.04 beta-2. I had just about given up hope.

I tried "User" mode but it didn't work, so I tried a factory reset on my monitor and it worked. Suddenly the "Detect monitor" button picked up my monitor and displayed all the correct resolutions / refresh rates.

Thank you again, I would never have thought that my monitor settings were culprit. (although I do know this monitor is not supported by Acer for XP at all which requires a powerstrip custom res workaround.)

---

