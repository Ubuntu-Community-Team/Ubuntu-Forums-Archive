---
title: "[SOLVED] USB Recognition???"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by SupLegolas on 2008-06-13
Hi,

I've had Ubuntu running on my desktop for a while, and decided to put Xubuntu on a relatively old laptop. For some reason, when I plug in a USB wireless adapter, it recognizes it under the command "lsusb", but it doesn't ask me to join a network or something. Granted, the adapter wasn't in during installation, but I think (x)ubuntu is more robust than that. Any advice would be appreciated. This concerns me as I cannot connect to my network after installing Xubuntu... It didn't happen in XP, so the USB port(s) is/are not the problem... I was thinking maybe there was a way to manually configure an unrecognized device from the Terminal, but I'm too much of a newbie to know how.

Thanks,

-Ian

Ubuntu 8.04 
Xubuntu 8.04

---

### Post by TeoBigusGeekus on 2008-06-13
Well, you've touched a very sensitive area here - Ubuntu and wireless support...
Search these forums with the name of your wireless adapter and if this doesn't give you any answers, then do a search for ndiswrapper - an application that will load window$ drivers in linux. After that.....:confused:

---

### Post by Sef on 2008-06-13
> Well, you've touched a very sensitive area here - Ubuntu and wireless support...

The problem is not Ubuntu, but the hardware companies.  If they open sourced their drivers, then there would not be a problem at all.

---

### Post by SupLegolas on 2008-06-13
Alright. Thanks you two, and I'll leave this thread open for a few more minutes in case anyone else has any input...

Thanks again,

-Ian

---

### Post by SunnyRabbiera on 2008-06-13
yeh wireless usb is tricky, but you can try to use ndiswrapper or something like that.

---

### Post by SupLegolas on 2008-06-13
Ahah! 

Got it to work by adding the apci=nopci option to the boot line!!! Works like a charm now! Thanks to everyone, and hopefully this will helps someone else too!

-Ian

---

