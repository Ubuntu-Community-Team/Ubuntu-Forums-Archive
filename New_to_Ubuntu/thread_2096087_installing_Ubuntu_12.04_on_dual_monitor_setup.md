---
title: "installing Ubuntu 12.04 on dual monitor setup"
date: 2012-12-19
forum: New to Ubuntu
---

### Post by blu juju on 2012-12-19
I'm new to Ubuntu and I'm having difficulties configuring a dual monitor  setup. Formerly this computer was running Win 2000  with Nvidia 7800gs  video adapter and just using Nvidia's software I could get my 2 CRT  monitors (Samsung SyncMaster & Viewsonic G90f) at the same  resolution (1280 x 1024 85 Hz) and slip windows from one monitor to the  other with mouseclick. 
The first time I installed Ubuntu 12.04 LTS I  could get 1280 x 1024 - 85 Hz on both monitors but it run quirky, for  instance the close/minimize/maximize buttons would always hide under the  top bar.  Things got messed up so I reinstalled, and I'm on my third  install but 1 monitor is at 1152 x 864  and 60 Hz can't go higher and is  now "unknown". Ubuntu still recognizes the Samsung and it's working OK.  BTW I have Nvidia Driver version 304.64. I would appreciate any tips  anyone could provide me, for instance where can I get a driver for the  Viewsonic monitor or is there some other way to get proper resolution on it?

---

### Post by blu juju on 2013-02-12
An update; I had left my computer on overnight and when returned only one monitor was on. I tried turning the power to the monitor on and off but that didn't solve the problem so I rebooted. Grub showed up on both monitors but after login I was back to one monitor again. So finally I started Nvidia settings. In the configuration the monitors were on top of each other so I dragged one over to the right, there were new resolution settings both monitors accepted 1280 x 1024 so I reset that. Now everything is set up the way I like, everything works great and is fixed but I have no idea why. It wasn't anything I did.

---

### Post by unheeding on 2013-02-12
> **blu juju said:**
> In the configuration the monitors were on top of each other so I dragged one over to the right, there were new resolution settings both monitors accepted 1280 x 1024 so I reset that. 

That's probably what did it.  When you have the displays set to mirror each other (like when they are on top of each other) it limits the resolution that you can use.

---

