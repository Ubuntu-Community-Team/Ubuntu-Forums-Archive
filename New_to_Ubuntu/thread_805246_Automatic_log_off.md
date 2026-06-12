---
title: "Automatic log off"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by cmcfarland21 on 2008-05-23
I have an ATI Radeon Xpress 200 video card. Ever since upgrading from 7.10 to Hardy 8.04 my system was sllllloooooowwwww.  So using Envy I remove my video card driver and everything is back to normal except Ubuntu logs itself off after a few minutes of no usage.  I can not figure out what is making it this occur.  Anyone have the same issue or know what is causing this.  IF I have my video driver installed this does not happen but I only get like 200 fps therefore every screen runs slow.

---

### Post by ubuntu-freak on 2008-05-24
There is a fix somewhere for slowness in Hardy with ATI graphics, I'll have a search.
 
Anywho, for the moment, navigate to System > Preferences > Power Management and disable the power saving options. Also, disable any screensavers that are set to run.
 
Nathan

---

### Post by cmcfarland21 on 2008-05-24
> **reassuringlyoffensive said:**
> There is a fix somewhere for slowness in Hardy with ATI graphics, I'll have a search.
 
Anywho, for the moment, navigate to System > Preferences > Power Management and disable the power saving options. Also, disable any screensavers that are set to run.
 
Nathan

It was the screensaver.  The screensaver was logging off my cpu.

Thanks a bunch.

---

### Post by ubuntu-freak on 2008-05-24
> **cmcfarland21 said:**
> It was the screensaver.  The screensaver was logging off my cpu.

Thanks a bunch.

 
No problem. 
 
There will be a new ATI proprietary driver in Hardy 8.04.1, so check that out in July, or whenever .1 is released.
 
Nathan

---

