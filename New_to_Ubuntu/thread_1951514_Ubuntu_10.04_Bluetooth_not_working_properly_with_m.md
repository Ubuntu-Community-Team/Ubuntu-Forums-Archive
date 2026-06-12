---
title: "Ubuntu 10.04: Bluetooth not working properly with my phone?"
date: 2012-04-02
forum: New to Ubuntu
---

### Post by Caffeinatrix on 2012-04-02
I'm trying to connect my phone (HTC Evo 4g, Android 2.3.3) to my laptop (Lenovo Ideapad) via Bluetooth and while the phone and laptop are seen as "paired" on the respective devices, it will not connect. Rather, it will connect for about a millisecond before it disconnects.
I have a feeling it is lack of drivers on Ubuntu, but I have no idea where to look to find the right ones (my Google-Fu is useless it seems).
There is the built-in Bluetooth adapter in my laptop, and I have been able to connect via Bluetooth on the Win7 side just fine.
What am I missing, has anyone else had this problem, and what can I do to fix this?

---

### Post by bcschmerker on 2012-04-02
What submodel of IdeaPad is involved?  I suspect that Lenovo® may have used a number of Bluetooth transceivers in production; according to [one discussion at Lenovo® Forums]("http://forums.lenovo.com/t5/IdeaPad-Y-U-V-and-Z-series/Bluetooth-Issue-solved-for-the-Ideapad-Y510-D2-laptop/td-p/13070"), several models, including the Y510-D2 the discussion cited, are picky about their transceivers.  Lacking further information on the issue, I have to presume that the finicky-hardware issue extends to all LinUX distros for portable computers, including Ubuntu® 10.04-LTS or later, as well as Microsoft® Windows® 6.0.60xx/6.1.76xx/7.0.80xx; hardware not certified for the computer in question by Lenovo® apparently results in a halt of the boot process, but I was unable to determine whether it was at the POST or OS-initialization level.

---

### Post by Caffeinatrix on 2012-04-02
It is the Lenovo IdeaPad Y570. I will go check out that forum now to see if it brings anything to light, thank you very much for the information :)

---

