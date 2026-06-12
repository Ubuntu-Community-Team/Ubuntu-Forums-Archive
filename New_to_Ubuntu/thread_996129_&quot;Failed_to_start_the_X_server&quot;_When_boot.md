---
title: "&quot;Failed to start the X server&quot; When booting ubuntu."
date: 2008-11-28
forum: New to Ubuntu
---

### Post by keeffecanflyit on 2008-11-28
My error is this:

"Failed to start the X server (Your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output diagnose the problem?"

I select Yes.

Spits this out:

/etc/gdm/failsafeXserver: line 47 [: too many arguements
Warning: Could not retrieve EDUD because get -edid is not installed (7).


The X server is now disabled, restart GDM when it is configured correctly. 


//==

The Ubuntu (7.10) doesn't load!
help the nooB! 
:guitar:


thanks in advance

---

### Post by cmnorton on 2008-11-29
For starters, boot into recovery mode.

run dpkg-reconfigure xserver-xorg

Accept all default settings, except as noted below.

At the resolution configuring screen add resolutions you think you will use including some lower ones like 1024x768 that you might not want to use.

When you get to the driver screen for now, I'd choose the vesa driver, not your proprietary driver, and I'm guessing you have an nvidia or something like that.

You are missing something to do with extended display, so, in addition please post info about your graphics processor and monitor.

---

