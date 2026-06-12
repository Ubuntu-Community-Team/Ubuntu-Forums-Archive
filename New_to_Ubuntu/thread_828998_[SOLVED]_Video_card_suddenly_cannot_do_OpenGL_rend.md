---
title: "[SOLVED] Video card suddenly cannot do OpenGL rendering!"
date: 2008-06-14
forum: New to Ubuntu
---

### Post by jasontu on 2008-06-14
After playing WoW for a couple of hours last night with no hiccups, I installed the latest Ubuntu updates and shut down the PC.  When I boot it up this morning it seems to not have any of the visual effects running, (just like before I even installed the video driver) and when I run glxinfo I receive a message that the test failed.

I am using an nVidia 6600 512mb video card using the 168 driver from the nVidia website - the latest one as of two weeks ago.

Could the updates have messed something up?  Could I just re-install the driver?  If I could just re-install the driver, do I have to clean out the previous one first?  If so, how?

Thank you

---

### Post by sdennie on 2008-06-14
If you are using drivers downloaded from the nvidia website, updates can sometimes break the OpenGL in the driver.  It's not incredibly common but, it does happen.  Just reinstalling the driver should fix the problem.

---

### Post by jasontu on 2008-06-18
Oddly enough I was able to uninstall the nVidia drivers using nVidia's own program and then re-install the driver with EnvyNG.

I was never able boot properly with the EnvyNG drivers before...

Strange.

---

