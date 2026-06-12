---
title: "Question on device support."
date: 2008-08-17
forum: New to Ubuntu
---

### Post by Kevin57 on 2008-08-17
I just ran Ubuntu Live CD on my Dell Latitude D830 laptop - very impressed. The wireless adaptor worked fine, connected to my access point, and I was able to access the Internet - wow !

Before I make the big jump - how will I know if all the hardware is supported and running efficiently - what is the linux equivalent of Windows Device Manager ? After installing Windows one has to install video/sound/chipset/bluetooth/wireless/etc. drivers specfic to the machine - surely Ubuntu cannot support *everything* from a single CD install ?!!!

---

### Post by nicedude on 2008-08-17
Most things are handled by system built in drivers. 2 categories are supported with a program called "jockey" which is the restricted drivers manager and can manage Video & Wifi drivers ( Only Nvidia & ATI Video all others supported by the system ). And anything else that is not supported by these means you will be building a driver from source for it ( almost nothing needs this and its not as hard as it sounds anyway ). But in general if the Live CD supports your stuff then you will have the same support once you install, the only thing I have seen people say messed up at that point is Wifi - which is only one device to have to mess with at worst.

Hope this info helps

---

