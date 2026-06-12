---
title: "graphics card enabled but not in use"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by Jake90 on 2008-09-15
Hey, my friend just installed hardy on his dell vostro 1000. Since he knows less about computers than me I'm trying to help him out.
His problem is that as soon as Ubuntu loads the login screen his screen is all messed up. It gets wavy and the image only takes up half the actual screen. at first I thought the problem was screen resolution, so I tried setting it. Both fields are blank and refused to be selected, I tried funding the screen automatically but it just blacked out when I did that. Afterword I checked the graphics card and saw it was enabled but not in use. I tried disabling and enabling, I was then told that I needed to restart in order for changes to take effect. I did that a couple pf times but the result is the same it is enabled but not in use... 
Thanks, any help is greatly appreciated

---

### Post by Jake90 on 2008-09-15
anyone?

---

### Post by Jake90 on 2008-09-16
bump

---

### Post by TheUbGuy on 2008-09-16
A little more information please ... what is the graphics card (make and model). What graphics driver is being used?

---

### Post by Jake90 on 2008-09-17
> **TheUbGuy said:**
> A little more information please ... what is the graphics card (make and model). What graphics driver is being used?
hey thanks or the reply
the graphics card is a ATI Radeon Xpress 256 MB HyperMemory (integrated)Radeon X1100. I am not sure about the driver. Whatever ubuntu uses by default I guess. How do I check this?
Thanks again 
Jake

---

### Post by TheUbGuy on 2008-09-17
You can check by System->Administration->Hardware Drivers. It will show if there is a hardware driver available and if it is enabled. If not, you can enable through there.

---

### Post by starcannon on 2008-09-17
Do what TheUbGuy said, and while your looking at that, be sure that the box is Checked, and Enabled. Sometimes it will report enabled even when the box is unchecked. It should then do a little downloading, installing, and then eventually it will ask you to reboot. Thats about it.

If that doesn't work, then you should try using envyng to setup and install the drive for you, its available in the {System>Administration>Synaptic Package Manager}

Welcome to Ubuntu!

---

### Post by Jake90 on 2008-09-21
> **TheUbGuy said:**
> You can check by System->Administration->Hardware Drivers. It will show if there is a hardware driver available and if it is enabled. If not, you can enable through there.

It says enabled but it's not in use. The driver is ATI fire gl. This is my main problem. I also can't access the internet due to the lack of a cable. The only way to access the internet is through wifi but unfortunately the wireless card driver doesn't work either. Thanks for all the help so far

---

### Post by Jake90 on 2008-09-24
anyone?

---

### Post by Paqman on 2008-09-24
> **Jake90 said:**
> I also can't access the internet due to the lack of a cable. The only way to access the internet is through wifi but unfortunately the wireless card driver doesn't work either.

Ok, I might be off on a complete tangent here, but how did you install the driver you've got if it wasn't from the internet? Normally you'd let the Hardware Drivers manager download and install the correct proprietary driver. EnvyNG does a similar job. So an internet connection is normally pretty important.

---

### Post by Jake90 on 2008-09-24
> **Paqman said:**
> Ok, I might be off on a complete tangent here, but how did you install the driver you've got if it wasn't from the internet? Normally you'd let the Hardware Drivers manager download and install the correct proprietary driver. EnvyNG does a similar job. So an internet connection is normally pretty important.

I didn't install any drivers, I am assuming that driver was installed when I installed Ubuntu

---

### Post by overdrank on 2008-09-24
> **Jake90 said:**
> I didn't install any drivers, I am assuming that driver was installed when I installed Ubuntu

Ok until you get a internet connection then installing drivers is out. Could you post the output of the command ```
lspci
``` in the terminal located under applications, accessories. This will identify your hardware and then a quick search may help to solve the issues.

---

