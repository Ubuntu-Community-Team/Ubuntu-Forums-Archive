---
title: "VisualBoy Advance makes my computer very slow"
date: 2013-02-19
forum: New to Ubuntu
---

### Post by Mr. ViC on 2013-02-19
Hi guys.

Trying to (legally) play Pokemon Blue using VBA.

Is there something I should change in order for the game to run faster?

It's weird that such an old game runs so slow. Using Ubuntu 12.04.

Thanks in advance!

---

### Post by gordintoronto on 2013-02-19
You're asking about a software package which has not been maintained for three years.

Have you tried gngb from the software centre?

What hardware are you running on? (CPU, memory, video)

---

### Post by Mr. ViC on 2013-02-19
> **gordintoronto said:**
> You're asking about a software package which has not been maintained for three years.

Have you tried gngb from the software centre?

What hardware are you running on? (CPU, memory, video)

Thanks for your reply!

Well I didn't know about it, sorry.

Tried GNGB but it doesn't seem to work very well. Are there any other alternatives? Also, here's what you asked for:

[IMG]http://i.imgur.com/deDvWf3.png[/IMG]

Thanks in advance!

---

### Post by Mr. ViC on 2013-02-20
Bumping. :)

---

### Post by fuorviatos on 2013-02-20
You're using a VESA driver, thus you don't have 3d acceleration enabled.
Show us the output of > lspci -vv|grep -i vga

---

### Post by Mr. ViC on 2013-02-20
> **fuorviatos said:**
> You're using a VESA driver, thus you don't have 3d acceleration enabled.
Show us the output of

Thanks for your reply!

Here it is:

[http://paste2.org/p/2921843](http://paste2.org/p/2921843)

Output was too big, had to post it there. :)

---

### Post by fuorviatos on 2013-02-20
Ok, you've got an ATi card. Let's see why the radeon driver doesn't get loaded in your Xorg log.
Type this and paste the output.
> sudo grep radeon /var/log/Xorg.0.log

---

### Post by Mr. ViC on 2013-02-20
> **fuorviatos said:**
> Ok, you've got an ATi card. Let's see why the radeon driver doesn't get loaded in your Xorg log.
Type this and paste the output.

Here is the output! :)

```
[    33.772] (II) LoadModule: "radeon"
[    33.773] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    33.773] (II) Module radeon: vendor="X.Org Foundation"
[    34.476] (II) UnloadModule: "radeon"
[    34.476] (II) Unloading radeon
```

---

### Post by fuorviatos on 2013-02-20
You radeon driver gets loaded then suddenly unloaded in Xorg, weird.
If you want a quick solution, try to install fglrx binary driver to get the 3rd acceleration

follow the steps here [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

If it helps, mark your thread as Solved please

---

### Post by Mr. ViC on 2013-02-20
It's working great now.

Thank you! :D

---

