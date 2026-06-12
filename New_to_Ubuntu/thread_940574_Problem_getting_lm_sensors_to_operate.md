---
title: "Problem getting lm_sensors to operate"
date: 2008-10-07
forum: New to Ubuntu
---

### Post by Chookah on 2008-10-07
Hi All :)

I'll start off by saying I ditched Vista and started using linux (Ubuntu) 3 days ago and i'm never going back!

Now for my (hopefully) small problem.

I've been trying to get lm_sensors operational.  On my first attempt I used apt-get to install the package and let it configure itself using *sensors-detect*.

Not knowing how to actually start the program I found xsensors in the add/remove menu.  Installed that but when I clicked the icon nothing happened.
Removed the package, downloaded the tarball and tried to compile it myself.  Couldn't get through the *make* process so I scrapped that idea.

Installed lm_sensors by apt-get again, went through the sensors-detect again and found (by chance) the command to start it was *sensors*.

Now I get this error:

[I]luke@chookah:~$ sensors
sensors: symbol lookup error: /usr/local/lib/libsensors.so.4: undefined symbol: sensors_lex_error[/I]

I tried to read and attempt as much as I could before posting for help, hopefully I havent made the problem worse!

---

### Post by philinux on 2008-10-07
If when you ran sensors detect it picked up and installed the sensors ok then all you need do is this. Right click on the bottom panel and choose add to panel. Scroll down and add Hardware Sensors.

---

### Post by Chookah on 2008-10-07
Hey thanks for your help, that worked! Its displaying GPU and CPU temps.
However i'm sure sensors detect found more then two sensors (like my motherboard & 2nd graphics card).

How can I check that it saved the detected setup properly? (and not currently running on a default setup)?

---

### Post by gandaran on 2008-10-07
> Right click on the bottom panel and choose add to panel. Scroll down and add Hardware Sensors.
if you have the sensors-applet intalled!

xsensors must have some kind of bug, doesn't work in hardy 8.04

---

### Post by philinux on 2008-10-07
> **Chookah said:**
> Hey thanks for your help, that worked! Its displaying GPU and CPU temps.
However i'm sure sensors detect found more then two sensors (like my motherboard & 2nd graphics card).

How can I check that it saved the detected setup properly? (and not currently running on a default setup)?

Right click the applet and select properties/preferences I cant remember off hand which it is.

---

### Post by phreon on 2008-10-08
Hi Folks,
I can run sensors and tries to install xsensors and sensor-applets. In the applications menu xsensors doesn't do anything, (wont run). I install sensor applets and cant find it anywhere. When I check the Synaptic Package Manager it says its installed.

What am I missing?
Thanks
P

---

