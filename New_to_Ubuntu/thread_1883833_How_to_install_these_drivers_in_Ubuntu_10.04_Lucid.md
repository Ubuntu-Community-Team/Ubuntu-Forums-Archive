---
title: "How to install these drivers in Ubuntu 10.04 Lucid LTS"
date: 2011-11-20
forum: New to Ubuntu
---

### Post by SkyLinePH on 2011-11-20
Hi, anyone can help me on how to install the following drivers, I'm using  Ubuntu 10.04 Lucid Lynx and tried to open the Hardware Drivers option in  System menu, but it doesn't detected my drivers.

[B]1. Graphics - Intel 82865g (Intel Extreme Graphics 2)
2. Sounds - C-Media Xear 3d Audio[/B]

I will wait for any feedbacks and comments. Thank you very much. :popcorn:

---

### Post by Perfect Storm on 2011-11-20
1. Graphics - Intel 82865g (Intel Extreme Graphics 2)

The Driver is installed by default. Nothing more to do.



2. Sounds - C-Media Xear 3d Audio

Do you have any sound?

---

### Post by SkyLinePH on 2011-11-20
I cant hear any sound.

*P.S.*

BTW Where can I see if my Graphic is installed?

---

### Post by mikewhatever on 2011-11-20
You can run the following in a terminal window:

```
lspci -k | grep -i kernel
```

As for the sound driver, where did you get it? Can you post the link?

---

### Post by SkyLinePH on 2011-11-20
I know my soundcard vendor because I'm using Windows XP before.

---

### Post by 3rdalbum on 2011-11-20
> **SkyLinePH said:**
> BTW Where can I see if my Graphic is installed?

Honestly, if you have an Intel graphics chip and you are seeing the Ubuntu desktop on your screen, then your graphics driver is installed. That's not the case for every driver, but for your particular Intel graphics it is. You see a desktop, you're using the drivers.

---

### Post by SkyLinePH on 2011-11-21
Thanks Sir 3rdalbum, but can you help me on how to install my soundcard manually. My soundcard is CMI8738 (C-Media XEAR 3D Audio).

---

