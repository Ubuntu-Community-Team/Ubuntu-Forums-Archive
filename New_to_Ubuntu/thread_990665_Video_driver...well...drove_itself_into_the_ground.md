---
title: "Video driver...well...drove itself into the ground."
date: 2008-11-22
forum: New to Ubuntu
---

### Post by Vunutus on 2008-11-22
So I wanted to get my video configured correctly on Ubuntu (all 3D stuff either lagged horribly or wouldn't work at all), so I went to the "Hardware Drivers" application. It showed my video card (geforce 6800), and began to download a driver package when I clicked on it. I let it finish, and it told me I needed to restart. I did so, and upon booting up again I have no video. It goes through grub fine but as soon as it gets to the point where it would load the video driver, everything goes blank and my monitor says "No Input Detected".

I have two questions:
1. How do I reset it? I presume I'll need to go into runlevel 1 and work from the command line, but I'm not sure how to do that from grub.
2. How am I supposed to update my driver?

---

### Post by oldrocker99 on 2008-11-22
Search Synaptic for EnvyNG, and let it autodetect your nVidia driver, after letting it deinstall the other driver. It will download your driver and install it, and you should be better off...

...I hope.

:guitar:

---

### Post by Vunutus on 2008-11-23
That sounds like a nifty program but before I can use it I need to somehow roll back my driver install so I can actually get something accomplished. If EnvyNG will run from a command line I could probably manage that, but the problem is I can't connect to the internet from the command line. I'm on dialup with a USB modem, which appears to not be supported by any command line ppp utilities (gnome-ppp is the only way I've been able to connect).

---

### Post by Vunutus on 2008-11-23
Bump. Does anyone know how I can roll back my driver installation?

---

### Post by Vunutus on 2008-11-24
Second bump. Maybe I'll just restate my problem and make a clearer thread if nobody sees this. I'd really like to get back to using Ubuntu :/

---

