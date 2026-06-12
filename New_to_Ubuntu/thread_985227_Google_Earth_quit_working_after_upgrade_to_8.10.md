---
title: "Google Earth quit working after upgrade to 8.10"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by raymondvillain on 2008-11-17
Just upgraded from Heron to Ibix.  Now when I launch Google Earth the graphics don't work correctly.  Insted of the earth's surface it shows patches of weird colors.

Any suggestions?

---

### Post by mikewhatever on 2008-11-17
Can you post the output of the following: **glxinfo | grep direct**
What's your video card? <sudo lshw -C display>

---

### Post by LowSky on 2008-11-17
you need to reinstall the graphics driver.

go to system > admin > restricted drivers

---

### Post by mihaiv on 2008-11-17
Disable desktop effects.

---

### Post by markjensen on 2008-11-17
It's worked for me without problems in my upgrade.

It might be related to desktop effects.   I don't use compiz or such eyecandy, so that would be one thing to look into.

---

### Post by mikewhatever on 2008-11-17
Google Earth works fine here with Compiz enabled, don't see why it shouldn't. I suspect the issue may be as detailed in the link below, but we won't know for sure unless the OP reveals the hardware in question.
[http://www.ubuntu.com/getubuntu/releasenotes/810#Upgrading](http://www.ubuntu.com/getubuntu/releasenotes/810#Upgrading)

---

### Post by raymondvillain on 2008-11-17
I opened a terminal and typed  
glxinfo | grep direct

and the output is 

direct rendering: Yes

When I type "sudo lshw -C display" I get the following:

  *-display UNCLAIMED     
       description: VGA compatible controller
       product: 82865G Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0

Does this mean anything to anybody?

---

### Post by mikewhatever on 2008-11-17
Well, the fist piece of information says you have graphical acceleration enabled, which is good because in that case you should be able to run Google Earth. However, the second piece says the graphics card is unclaimed, not sure why. How about the following output:
<glxinfo | grep OpenGL>

---

